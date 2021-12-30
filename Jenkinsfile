define NAME;
define DEPLOYMENT_ENV_tmp;
define CONFIG_TYPE_tmp;
pipeline 
{
    agent any 
    
    stages 
    {
    	stage('Pre-setup')
        {
        	steps
        	{
        		script
        		{
        			switch(params.ENV)
        			{
        				case 'dev':
        					echo 'Deploying to dev env'
        					//NAME="Johns App"
        					DEPLOYMENT_ENV_tmp="Sandbox"
        					CONFIG_TYPE_tmp="dev"
        					break
        				case 'prod':
        					echo 'Deploying to production env'
        					//NAME="Johns App"
        					DEPLOYMENT_ENV_tmp="Sandbox"
        					CONFIG_TYPE_tmp="prod"
        					break
        			}
        		}
        	}
        }
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
        	environment
        	{
        		APP_NAME="app"
        		DEPLOYMENT_ENV="${DEPLOYMENT_ENV_tmp}"
        		CONFIG_TYPE="${CONFIG_TYPE_tmp}"
        	}
        	steps
        	{
        		script
        		{
        			switch(params.ENV)
        			{
        				case 'dev':
        					echo 'Deploying to dev env'
        					withCredentials([usernamePassword(credentialsId: 'johnpowerlogin', passwordVariable: 'PLATFORM_PASSWORD', usernameVariable: 'PLATFORM_USERNAME')]) {
							    bat 'mvn -X -e deploy -Dmuledeploy'
							}
        					break
        				case 'prod':
        					echo 'Deploying to production env'
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