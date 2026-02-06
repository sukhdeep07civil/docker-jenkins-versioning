pipeline {
    agent any

    environment{
        IMAGE_NAME = "ssm0712/myapp"
        TAG = "${BUILD_NUMBER}"
    }


    stages{
        stage('Docker Login'){
            steps{
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]){
                    bat "docker login -u %DOCKER_USER% -p %DOCKER_PASS%"
                }
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
