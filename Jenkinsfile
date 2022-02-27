pipeline { 
    environment { 
        AWS_ACCOUNT_ID="295317182281"
        AWS_DEFAULT_REGION="us-east-2" 
        IMAGE_REPO_NAME="nodejs-build"
        IMAGE_TAG=""
        registry = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}"
        dockerImage = '' 
	registryCredential = 'ecr-cred'
    }
    agent any 
      stages { 
	stage('Git') {
		steps {
			git 'https://github.com/SWAGATAM04/nodejs.git'
	           }
	}
	stage('Build') {
		steps {
			sh 'npm install'
	              }
	}
	stage('Test') {
	        steps {
			sh 'npm test'
		      }
	}
	
	
        
	stage('Building our image') { 
            steps { 
                script { 
			dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            } 
        }
        stage('Pushing to ECR') { 
            steps { 
                script { 
			 docker.withRegistry('https://295317182281.dkr.ecr.us-east-2.amazonaws.com', 'ecr:us-east-2:ecr-cred') {
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
      
	 stage('Deploy Image to ECS'){
		 steps {
			 sh "sh deploy.sh"
   }
}	
    
      }
}
