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
