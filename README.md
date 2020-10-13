# QAC SFIA2 Project

Starting my README work.

## Contents

- [Brief](#Brief)
- [Technologies utilised](#Technologies-utilised)
- [Moscow Approach](#Moscow-Approach)
- [Risk Assessment](#Risk-Assessment)
- [Future Improvements](#Future-Improvements)

## Brief

I was given the task to deploy a working flask application. The project mainly focused on increasing the efficiency of the automation of deploying the flask application. Throughout this README I will be going over the tools utilised throughout the practical project.


## Technologies utilised 
Below I have listed the technologies I have implemented throughout this project. 

 - Kanban Board: Jira
 - Version Control: Git
 - CI Server: Jenkins
 - Configuration Management: Ansible
 - Cloud Server: AWS EC2
 - Database Server: AWS RDS
 - Containerisation: Docker
 - Reverse Proxy: NGINX
 - Orchestration Tool: Kubernetes
 - Infrastructure Management: Terraform

### Kanban Board: Jira

I used the Kanban Board: Jira to help me breakdown the project into smaller tasks. I then organised each task in accordance to how I wanted to progress throughout the completion of the project. I factored in the time and difficulty needed of each task. Having this Jira board also helped plan out my project.

### Cloud Server: AWS EC2

For my cloud server I chose to work with Amazon Web Services and their EC2 instance to launch my virtual machine. When launching an instance I configured the security groups and the ports accessible to it. Also assigning the storage space needed before working on the project aided me to work freely. 

### Reverse Proxy: NGINX

My choice of reverse proxy was NGINX. As already being familiar with the reverse proxy it was easier for me to implement it to my project, its functionality in regards to my project acted as a reverse proxy and a load balancer.

## Moscow Approach

The MOSCOW approach was utilised to ensure all the important features of the practical project was concentrated on.

- ### Must Contain
1. Using Ansible to configure jenkins on a virtual machine
2. The reverse proxy used will be NGINX
3. There has to be 2 databases, first for deployment and second for testing
4. There needs to be an automated testing that takes place when a new update is made. 
- ### Should Contain
1. The jenkins pipeline include a webhook connecting to github/gitlab
2. Ensure all secret texts are hidden at all times
3. Deployed on Kubernetes Cluster
- #### Could Contain
1. The utilisation of Terraform integrated throughout the deployment. 
2. RDS connection
- ### Won't Contain
1. The capability to deploy all the necessary applications with a few commands
2. Won't be utilising more pods and containers 
3. The capability to rollback to previous versions.

## Risk Assessment

Assessing risks is a very important matter throughout the development
of any project. When creating a project each step has its own potential risks associated with it and it is vital these potential
risks are identified and solutions are made to prevent them from being exploited. Below I have attached a table highlighting the various risks.

## Future Improvements

Throughout this project I have realised there were some improvements I could have made at different sections. 

Going to add more future improvements.
End.

