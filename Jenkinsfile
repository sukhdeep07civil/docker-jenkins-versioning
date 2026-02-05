pipeline{
    agent any

    environment{
        IMAGE_NAME = "ssm0712/myapp"
        TAG = "${BUILD_NUMBER}"
    }

    stages{
        stage('Delete Old Containers'){
            steps{
                bat '''
                docker rm -f $(docker ps -q) || exit 0
                '''
            }
        }

        stage('Build Docker Image'){
            steps{
                bat '''
                docker build -t %IMAGE_NAME%:%TAG% .
                '''
            }
        }

        stage('Push Versioned Image'){
            steps{
                bat '''
                docker push %IMAGE_NAME%:%TAG%
                '''
            }
        }
    }
}
