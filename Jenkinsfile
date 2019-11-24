pipeline {
  agent any
  stages {
    stage('Build and Test') {
      environment {
        ENV_FILE = credentials('7c4810c3-d0a8-4dff-b634-ca6aea6f8e3c')
      }
      steps {
        sh 'docker-compose build --no-cache'
      }
    }
    stage('Deploy Master'){
      when {
        expression { BRANCH_NAME == 'master' }
      }
      environment {
        ENV_FILE = credentials('7c4810c3-d0a8-4dff-b634-ca6aea6f8e3c')
      }
      steps {
        sh 'docker-compose down'
        sh 'docker-compose up -d'
      }
    }
  }
}