stage('Cloning Git'){
					steps {
						script{
							sh 'https://github.com/Sumanth5/case-study' 
						}		
					}
				}
				stage('Build docker image ') {
					steps {
						script {
							sh 'docker image build -t $DOCKER_HUB_REPO:latest .'
							sh 'docker image tag $DOCKER_HUB_REPO:latest $DOCKER_HUB_REPO:$BUILD_NUMBER'
							echo "image buit successfuly"
						}
					}	
				}
			       stage('Push Docker Image') {
                    
                            checkout scm

                            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {

                                def customImage = docker.push("sumanth55/kubes")

                
                                customImage.push()
                            }
                    }