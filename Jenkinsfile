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
                sh 'docker stop gadget-container || true'
                sh 'docker rm gadget-container || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8088:80 --name gadget-container gadgetstore-app'
            }
        }
    }
}
