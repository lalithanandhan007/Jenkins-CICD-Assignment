pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t studentapp:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat '''
                docker stop studentweb || exit /b 0
                docker rm studentweb || exit /b 0
                '''
            }
        }

        stage('Run New Container') {
            steps {
                bat 'docker run -d --name studentweb -p 8080:80 studentapp:v1'
            }
        }
    }
}