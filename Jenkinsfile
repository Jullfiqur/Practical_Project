pipeline{
        agent any
        stages{
            stage('Build'){
                steps{
                    sh "sudo docker-compose build"
		    sh "sudo docker-compose up -d"
                }
            }
        
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

	    stage('Vm onto new machine'){
		steps{
		     withCredentials([file(credentialsId:'AWSfirst',variable:'pemkey')]){
		     sh '''
			echo $pemkey
			ssh -tt -o "StrictHostKeyChecking=no" -i $pemkey ubuntu@ec2-18-222-137-146.us-east-2.compute.amazonaws.com << EOF
			mkdir sshworks
			git clone https://github.com/Jullfiqur/Practical_Project.git
			cd Practical_Project
			docker-compose up
			pytest


			EOF
		     '''
			}
		
		}
	    }
	}
} 
