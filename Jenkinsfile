pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('deploy') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input '<"proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}