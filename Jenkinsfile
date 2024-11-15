pipeline {
    agent any

    environment {       
        BUILD_DIR = 'D:/Deployment/WebApiJen' // Local directory for publishing     
    }

    stages {
        stage('Checkout Code') {
            steps {
               
                checkout scm
            }
        }

        stage('Build') {
            steps {
		script{
			
                	bat "dotnet restore"
			bat "dotnet build --configuration Release"

		}
               
            }
        }
       

        stage('Publish') {
            steps {
		script{              
                bat "dotnet publish -c Release -o ${BUILD_DIR}"
		}
            }
        }

        
    }

    post {
        success {
            echo 'Build and deployment completed successfully!'
        }
        failure {
            echo 'Build or deployment failed. Check the logs.'
            // Optionally, send failure notifications here
        }
    }
}
