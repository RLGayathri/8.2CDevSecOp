pipeline {
  agent any

  environment {
    PATH = "/Users/rlgayathri/.nvm/versions/node/v22.14.0/bin/npm"
    SHELL = "/bin/bash"
  }

  stages {
    stage('Checkout') {
      steps {


    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('Run Tests') {
      steps {
        sh 'npm test || true'
      }
    }

    stage('Generate Coverage Report') {
      steps {
        sh 'npm run coverage || true'
      }
    }

    stage('NPM Audit (Security Scan)') {
      steps {
        sh 'npm audit || true'
      }
    }
      }
    }
  }
}