pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t healthcareapp:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop healthcare-container || true'
                sh 'docker rm healthcare-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 80:80 --name healthcare-container healthcareapp:v1'
            }
        }
    }
}