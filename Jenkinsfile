pipeline {
  environment {
    registry = "sonpham170199/nodejs"
    registryCredential = 'dockerhub_id'
    dockerImage = "sonpham170199/nodejs"
    docker_username = sonpham170199
    docker_password = Ilab.vn171
  }
  agent any
  stages {
    stage('Building Image') {
      steps {
            sh "docker build -t $dockerImage -f Dockerfile ."
      }
    }
    stage('Login to Registry') {
      steps {
            sh "docker login -u=$docker_username -p=$docker_password"
      }
    }
    stage('Push Image') {
      steps {
            sh "docker push $registry:$BUILD_NUMBER"
      }
    }
  }
}