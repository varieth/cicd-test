pipeline {

    agent any 
    
    stages {
        stage('Build') { 
            steps {
               sh 'mvn -X -e clean install'
            }
        }
    }
}