pipeline {
  environment {
    registry = "sonpham170199/nodejs"
    registryCredential = 'dockerhub_id'
    dockerImage = "sonpham170199/nodejs"
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
            git branch: 'main',
                url: 'https://github.com/TheFirstShogun99/nodejs.git'
      }
    }
  }
}