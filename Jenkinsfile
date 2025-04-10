pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
        sh 'git --version'
      }
    }

    stage('Build') {
      steps {
        sh 'echo "Building..."'
        sh 'ls -la'
      }
    }

    stage('Docker Operations') {
      steps {
        script {
          sh """
          echo "Logging in to Docker Hub"
          docker login -u ${DOCKERHUB_CREDENTIALS_USR} -p ${DOCKERHUB_CREDENTIALS_PSW}
          """
        }

      }
    }

  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub-cred')
  }
  post {
    always {
      echo 'Pipeline completed'
    }

  }
}