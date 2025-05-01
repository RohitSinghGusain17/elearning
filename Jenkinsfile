pipeline {
  agent any

  environment {
    BACKEND_DIR = "backend"
    FRONTEND_DIR = "frontend"
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/RohitSinghGusain17/elearning.git' // Update with your repo
      }
    }

    stage('Install Backend Dependencies') {
      steps {
        dir("${BACKEND_DIR}") {
          bat 'npm install'
        }
      }
    }

    stage('Install Frontend Dependencies') {
      steps {
        dir("${FRONTEND_DIR}") {
          bat 'npm install'
        }
      }
    }

    stage('Build Frontend') {
      steps {
        dir("${FRONTEND_DIR}") {
          bat 'set "CI=false" && npm run build'
        }
      }
    }

    stage('Build Docker Images') {
      steps {
        bat 'docker-compose build'
      }
    }

    stage('Run Containers') {
      steps {
        bat 'docker-compose up -d'
      }
    }

    stage('Verify') {
      steps {
        bat 'docker ps' // Check running containers
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
    cleanup{
      echo 'Pipeline cleaned up!'
      bat 'docker-compose down'
    }
  }
}
