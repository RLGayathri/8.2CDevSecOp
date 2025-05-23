pipeline {
  agent any

 environment {
    PATH = "/Users/rlgayathri/.nvm/versions/node/v22.14.0/bin:$PATH"
    SHELL = "/bin/bash"
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/RLGayathri/8.2CDevSecOp.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Run Tests') {
      steps {
        catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
          sh 'npm test'
        }
        emailext subject: "Test Stage Status: ${currentBuild.currentResult}",
                 body: "Test stage result: ${currentBuild.currentResult}",
                 to: 'gayatrirayudu123@gmail.com',
                 attachLog: true
      }
    }

    stage('Generate Coverage Report') {
      steps {
        sh 'npm run coverage || true'
      }
    }
  }
}