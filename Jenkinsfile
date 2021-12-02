pipeline {

    agent any 
    
    stages {
        stage('Build') { 
            steps {
               bat 'mvn -X -e clean install'
            }
        }
    }
}