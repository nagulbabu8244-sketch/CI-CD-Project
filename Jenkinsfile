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
                bat 'docker stop cicd-container || exit 0'
                bat 'docker rm cicd-container || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8081:80 --name cicd-container cicd-demo'
            }
        }

    }
}