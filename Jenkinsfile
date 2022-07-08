pipeline {   
  agent{      
    node { label 'slave'}     
  }  
  environment {     
    DOCKERHUB_CREDENTIALS= credentials('b3e3cdad-bb85-47d7-95d8-0553dcda63b2')     
  }
  stage('Build') {
    steps {
        sh 'yum check-update -y'
		sh 'curl -fsSL https://get.docker.com/ | sh'
		sh 'sudo systemctl start docker'
		sh 'sudo systemctl status docker'
		sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
		sh 'sudo chmod +x /usr/local/bin/docker-compose'
		sh 'docker-compose --version'
            }
        }  
  stages {         
    stage("Git Checkout"){           
      steps{                
	git credentialsId: 'github', url: 'https://github.com/TheFirstShogun99/nodejs.git'                 
	echo 'Git Checkout Completed'            
      }        
    }
    stage('Build Docker Image') {         
      steps{                
	sh 'sudo docker build -t sonpham170199/nodejs:$BUILD_NUMBER .'           
        echo 'Build Image Completed'                
      }           
    }
    stage('Login to Docker Hub') {         
      steps{                            
	sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'                 
	echo 'Login Completed'                
      }           
    }               
    stage('Push Image to Docker Hub') {         
      steps{                            
	sh 'sudo docker push dockerhubusername/dockerhubreponame:$BUILD_NUMBER'                 echo 'Push Image Completed'       
      }           
    }      
  } //stages 
  post{
    always {  
      sh 'docker logout'           
    }      
  }  
} //pipeline
