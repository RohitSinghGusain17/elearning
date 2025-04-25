pipeline {
    agent any

    environment {
        BACKEND_PATH = 'backend'
        FRONTEND_PATH = 'frontend'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your/repo.git'
            }
        }

        stage('Build Docker Containers') {
            steps {
                script {
                    // Stop existing containers
                    sh 'docker-compose down'

                    // Build images
                    sh 'docker-compose build'
                }
            }
        }

        stage('Deploy Services') {
            steps {
                script {
                    // Start containers
                    sh 'docker-compose up -d'
                }
            }
        }

        stage('Cleanup Unused Images/Containers') {
            steps {
                sh 'docker system prune -af'
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed!'
        }
    }
}
