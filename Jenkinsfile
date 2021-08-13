pipeline {
    agent{
        label 'linux'
    }
    tools {
      maven 'mvn_3.8.1'
      }
    stages {
        stage ('Checkout Java Code'){
            steps{
                git branch: 'master', credentialsId: 'GITHUB-CREDS', url: 'https://github.com/kul-samples/java_sample_webapp.git'
            }
        }  
        stage('Build Package') {
            steps {
                sh 'mvn clean package'
            }
            post {
              always {
                archive 'target/devops.war'
            }
          }
        }
        stage('Create Docker Image') {
            steps {
                sh '''docker image ls 
                    docker image build .  -f Dockerfile -t msantoshdocker/devops:latest
                    docker image ls'''
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker push msantoshdocker/devops:latest'
                  
            }
        }
        stage ('SAST'){
          parallel{
            stage ('sonar-scan'){
              steps {
                echo 'Running Sonar Scan'
              }
            }
            stage ('synk-scan'){
              steps {
                echo 'Synk scan'
              }
            }
            stage ('DC'){
              steps {
                echo 'Running Dependency Check'
              }
            }
          }
        }
    }
}
