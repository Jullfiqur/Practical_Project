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

	    stage('Docker-compose Install'){
		steps{
		    sh '''
		    sudo apt update
		    sudo apt install -y curl jq
		    version=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r '.tag_name')
		    sudo curl -L "https://github.com/docker/compose/releases/download/${version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
		    sudo chmod +x /usr/local/bin/docker-compose

		    '''
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
			sudo apt update
			sudo apt install -y curl jq
			version=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r '.tag_name')
			sudo curl -L "https://github.com/docker/compose/releases/download/${version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
			sudo chmod +x /usr/local/bin/docker-compose
			sudo -E DATABASE_URI=$DATABASE_URI SECRET_KEY=$SECRET_KEY MYSQL_ROOT_PASSWORD=$MYSQL_ROOT_PASSWORD docker-compose up -d



		#	pytest


			EOF
		     '''
			}
		
		}
	    }
	}
} 
