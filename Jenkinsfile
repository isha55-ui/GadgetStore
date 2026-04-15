pipeline {
    agent any

    environment {
        IMAGE_NAME = "ecommerce-app"
        CONTAINER_NAME = "ecommerce-container"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }

        stage('Stop Old Container') {
            steps {
                script {
                    sh 'docker stop $CONTAINER_NAME || true'
                    sh 'docker rm $CONTAINER_NAME || true'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8080:80 --name $CONTAINER_NAME $IMAGE_NAME'
                }
            }
        }
    }
}
