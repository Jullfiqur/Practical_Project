pipeline{
        agent any
        stages{
            stage('Build'){
                steps{
                    sh "sudo docker-compose build"
		    sh "sudo docker-compose up -d"
                }
            }
        }    
	    stage('Docker install')
		steps{
		     sh "curl https://get.docker.com | sudo bash"
		}
	    stage('Add docker user to group')
		steps{
		     sh "sudo usermod -aG docker $(whoami)"
		}
	   

	    stage('Clone practical_project git repo')
		steps{
		     sh "git clone https://github.com/Jullfiqur/Practical_Project.git"
		}
} 
