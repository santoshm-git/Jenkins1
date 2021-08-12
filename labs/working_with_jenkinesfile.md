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
