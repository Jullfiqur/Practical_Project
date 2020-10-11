pipeline{
        agent any
        stages{
	    stage('Docker install'){
		steps{
		     sh "curl https://get.docker.com | sudo bash"
		}
	    }

	    stage('Add docker user to group'){
		steps{
		     sh "sudo usermod -aG docker $(whoami)"
		}
	    }
            
            stage('Clone practical_project git repo'){
                steps{
                     sh "git clone https://github.com/Jullfiqur/Practical_Project.git"
                }
            }

	    stage('Docker compose build'){
		steps{
		    sh "sudo docker-compose build"
	        }
            }

	    stage('Docker compose run'){
		steps{
		    sh "sudo docker-compose up -d"
		}
	    }

	    stage('VM onto new machine'){
		steps{
		     withCredentials([file(credentialsId:'AWSfirst',variable:'pemkey')]){
		     sh '''
			echo $pemkey
			ssh -tt -o "StrictHostKeyChecking=no" -i $pemkey ubuntu@ec2-18-222-137-146.us-east-2.compute.amazonaws.com << EOF
			git clone https://github.com/Jullfiqur/Practical_Project.git
			cd Practical_Project
			curl https://get.docker.com | sudo bash
			sudo usermod -aG docker $(whoami)
			docker-compose build
			docker-compose up
			pytest


			EOF
		     '''
			}
		
		}
	    }
	}
} 
