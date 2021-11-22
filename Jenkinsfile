pipeline {
    agent any 
    enviornment{
    USERNAME='%APUSER%'
    PASSWORD='%AP_PASS%'
    TESTVARIABLE='%TESTVAR%'
    ENVIRONMENT='%ENV%'
    
    }
    stages {
        stage('Build') { 
            steps {
               bat 'mvn -X -e clean install'
            }
        }
        stage('Deploy') { 
            steps {
                bat 'mvn package deploy -DmuleDeploy -e -X -Denv=%ENVIRONMENT% -Danypoint.username=%USERNAME% -Danypoint.password=%PASSWORD% -Dtest.var=%TESTVARIABLE%'
            }
        }
    }
}