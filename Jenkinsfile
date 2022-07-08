pipeline { 
    environment { 
        registry = "sonpham170199/nodejs" 
        registryCredential = 'dockerhub_id' 
        dockerImage = 'nodejs' 
    }
    agent slave 
    stages { 
        stage('Install Packages') { 
            steps { 
                sh 'yum update -y'
                sh 'curl -fsSL https://get.docker.com/ | sh'
                sh 'sudo systemctl start docker'
                sh 'sudo systemctl status docker'
            }
        }
    stages { 
        stage('Cloning our Git') { 
            steps { 
                git 'https://github.com/TheFirstShogun99/nodejs.git' 
            }
        }
        stage('Building our image') { 
            steps { 
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 
                }
            } 
        }
        stage('Deploy our image') { 
            steps { 
                script { 
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push() 
                    }
                } 
            }
        } 
        stage('Cleaning up') { 
            steps { 
                sh "docker rmi $registry:$BUILD_NUMBER" 
            }
        } 
    }
}
