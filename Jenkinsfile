pipeline {
  environment {
    registry = "sonpham170199/nodejs"
    registryCredential = 'dockerhub_id'
    dockerImage = "sonpham170199/nodejs"
  }
  agent any
  stages {
    stage('Building Image') {
      steps {
            sh "docker --version"
      }
    }
  }
}