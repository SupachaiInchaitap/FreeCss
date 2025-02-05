pipeline {
    agent any
    stages {      
        stage("Copy files to Docker server") {
            steps {
                // Ensure the workspace files are copied to the remote server
                sh "scp -r /var/lib/jenkins/workspace/66026190/* root@43.208.241.236:~/66026190"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                // Execute the build Ansible playbook
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66026190/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                // Execute the deployment Ansible playbook
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66026190/playbooks/deploy.yaml'
            }    
        } 
    }
}
