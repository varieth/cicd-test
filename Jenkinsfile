pipeline {

    agent any 
    
    stages {
        stage('Build') { 
            steps {
               echo 'Hello World'
               bat 'mvn -e -X clean package'
            }
        }
    }
}