pipeline {
    agent any

    environment{
        IMAGE_NAME = "ssm0712/myapp"
        TAG = "${BUILD_NUMBER}"
    }

    stages{
        stage('delete old containers'){
            steps{
                bat 'for /f "tokens=*" %%i in (''docker ps -q'') do docker rm -f %%i'
            }
        }

        stage('build docker image'){
            steps{
                bat 'docker build -t %IMAGE_NAME%:%TAG% .'
            }
        }

        stage('push docker image to dockerhub'){
            steps{
                bat 'docker push %IMAGE_NAME%:%TAG%'
            }
        }

    }
}
