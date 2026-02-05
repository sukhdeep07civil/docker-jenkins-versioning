pipeline {
    agent any

    environment{
        IMAGE_NAME: "ssm0712/myapp"
        TAG: "${BUILD_NUMBER}"
    }

    stages{
        stage('Delete old containers'){
            steps{
                bat '''
                docker rm -f $(docker ps -q) || exit 0

                '''
            }
        }
        stage('Build docker image'){
            steps{
                bat '''
                docker build -t %IMAGE_NAME%:%TAG%
                '''
            }
        }

        stage('Push versioned docker image'){
            steps{
                bat '''
                docker push %IMAGE_NAME%:%TAG%
                
                '''
            }
        }
    }
}