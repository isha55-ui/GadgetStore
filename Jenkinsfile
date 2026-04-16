pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t gadgetstore-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop gadgetstore-container || true'
                sh 'docker rm gadgetstore-container || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8090:80 --name gadgetstore-container gadgetstore-app'
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful'
        }
        failure {
            echo 'Deployment Failed'
        }
    }
}
