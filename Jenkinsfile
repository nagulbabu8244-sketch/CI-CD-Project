pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t cicd-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat '''
                docker stop cicd-container || exit /b 0
                docker rm cicd-container || exit /b 0
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 8081:80 --name cicd-container cicd-demo'
            }
        }
    }
}