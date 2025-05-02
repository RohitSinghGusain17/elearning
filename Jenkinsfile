pipeline {
    agent any

    environment {
        BACKEND_DIR = "backend"
        FRONTEND_DIR = "frontend"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/RohitSinghGusain17/elearning.git'
            }
        }

        stage('Install Dependencies (only once)') {
            steps {
                bat 'cd frontend && npm install'
                bat 'cd backend && npm install'
            }
        }

        stage('Start Services') {
            steps {
                bat 'docker-compose up -d'
            }
        }

        stage('Verify') {
            steps {
                bat 'docker ps'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}