define APP_NAME
define DEPLOYMENT_ENV
define CONFIG_TYPE
pipeline 
{
    agent any 
    
    stages 
    {
        stage('Build') 
        { 
            steps 
            {
               echo 'Building'
               bat 'mvn -e -X clean package'
            }
        }
        stage('Deploy')
        {
        	steps
        	{
        		script
        		{
        			switch(params.ENV)
        			{
        				case 'dev':
        					echo 'Deploying to dev env'
        					APP_NAME="Johns App"
        					DEPLOYMENT_ENV="Sandbox"
        					CONFIG_TYPE="dev"
        					withCredentials([usernamePassword(credentialsId: 'johnpowerlogin', passwordVariable: 'PLATFORM_PASSWORD', usernameVariable: 'PLATFORM_USERNAME')]) {
							    bat 'mvn -X -e deploy -Dmuledeploy'
							}
        					break
        				case 'prod':
        					echo 'Deploying to production env'
        					APP_NAME="Johns App"
        					DEPLOYMENT_ENV="Sandbox"
        					CONFIG_TYPE="prod"
        					withCredentials([usernamePassword(credentialsId: 'johnpowerlogin', passwordVariable: 'PLATFORM_PASSWORD', usernameVariable: 'PLATFORM_USERNAME')]) {
							    bat 'mvn -X -e deploy -Dmuledeploy'
							}
        					break
        			}
        		}
        	}
        }
    }
}