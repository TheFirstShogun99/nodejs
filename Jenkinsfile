pipeline {
  environment {
    registry = "sonpham170199/nodejs"
    registryCredential = 'dockerhub_id'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
            git branch: 'main',
                url: 'https://github.com/TheFirstShogun99/nodejs.git'
      }
    }
    stage('Building image') {
      steps{
        steps {
          sh 'buildah bud -t docker.io/$registry:$BUILD_NUMBER .'
        }
      }
    }
    stage('Push image') {
      steps{
        steps {
          sh 'buildah login -u sonpham170199 -p Ilab.vn171 docker.io'
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "buildah rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}