pipeline {

    agent any 
    
    stages {
        stage('Build') { 
            steps {
               bat 'mvn -X -e clean install'
            }
        }
        stage('Deploy') { 
            steps {
            	echo "Testing build %ENV% "
                bat 'mvn package deploy -DmuleDeploy -e -X -Denv="%ENV%" -Danypoint.username="%APUSER%" -Danypoint.password="%AP_PASS%" -Dtest.var="%TESTVAR%"'
            }
        }
    }
}