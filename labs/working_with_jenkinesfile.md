### Create pipeline job in Jenkins
1. Got Jenkins dashboard and select 'New Item'
2. Add 'Name' as 'firstPipeline' and select 'Pipeline' Options and click ok
3. Scroll to 'Pipeline' and Select 'Hellow World' under 'try Sample pipeline'
4. Click 'Save' & then Click Build Now

### Sample code for Hello World

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}

### Adding more stages to the pipeline
1. Configure your build
2. Go to pipeline & update pipeline code with below code:

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('how are you') {
            steps {
                echo 'how are you'
            }
        }
    }
}

### Adding parallel stages in Jenkinsfile
1. update pipeline code with below code:

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('How are you?') {
            steps {
                echo 'How are you?'
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
![image](https://user-images.githubusercontent.com/64212984/129163258-3528ca87-2dee-447a-857f-861280c6b86f.png)


### Take pipeline from SCM (GITHUB)
1. Edit the build and select Definations as 'Pipeline Script from SCM' under pipeline
2. Under SCM select Git
3. Under Repository URL add Github repo where Jenkinsfile is avaiable, https://github.com/santoshm-git/Jenkins1.git
4. Under Credentials select Github-creds
5. Under Branches to build add */main
6. Under Script Path add the name of pipeline script, like Jenkinsfile

###Sample stage view
![Declarative_stageview](https://user-images.githubusercontent.com/64212984/129164869-677f29c6-e855-4356-9c95-d253f752e789.PNG)

### Using pipeline syntex
1. Go to the pipeline build 'http://18.237.87.185:8080/job/firstPipeline/'
2. Select 'Pipeline Syntex', Select 'Snippet Generator' 
3. Under 'Sample Step' select 'git: Git'
4. Add ''Repository URL' as https://github.com/kul-samples/java_sample_webapp.git, branch as main, Credentials as Github credentials.
5. Click on 'Generate Pipeline Script' to prepare pipeline  step
6. Copy the synxtax and add the same in Jenkinsfile using below code:

pipeline {
    agent any

    stages {
      stage ('Checkout AWS'){
            steps{
                git branch: 'main', credentialsId: 'GITHUB-CREDS', url: 'https://github.com/santoshm-git/aws-labs.git'
            }
        }  
       stage ('Checkout Java Code'){
            steps{
                git branch: 'main', credentialsId: 'GITHUB-CREDS', url: 'https://github.com/kul-samples/java_sample_webapp.git'
            }
        }
        .....
        .....