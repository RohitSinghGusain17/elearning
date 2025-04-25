pipeline {
    agent any

    environment {
        FRONTEND_DIR = 'frontend'
        BACKEND_DIR = 'backend'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/RohitSinghGusain17/elearning.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                echo 'Building Docker Images for Frontend and Backend'
                sh 'docker-compose build'
            }
        }

        stage('Run Containers') {
            steps {
                echo 'Starting Docker Containers'
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
