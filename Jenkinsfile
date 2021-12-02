pipeline {

    agent any 
    
    stages {
        stage('Build') { 
            steps {
               echo 'Hello World'
               sh 'mvn -e -X clean install'
            }
        }
    }
}