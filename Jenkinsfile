pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Deeksha-chouhan/devops-ci-cd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-webapp .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop devops-container || true'
                sh 'docker rm devops-container || true'
            }
        }

        stage('Deploy New Container') {
            steps {
                sh 'docker run -d -p 8082:80 --name devops-container devops-webapp'
            }
        }
    }
}
