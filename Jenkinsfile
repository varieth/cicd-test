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
        	environment
        	{
        		APP_NAME="app"
        		DEPLOYMENT_ENV="Sandbox"
        		CONFIG_TYPE="dev"
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