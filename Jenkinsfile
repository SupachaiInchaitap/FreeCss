pipeline {
    agent any
    stages {      
        stage("Copy files to Docker server") {
            steps {
                // Ensure the workspace files are copied to the remote server
                sh "scp -r /var/lib/jenkins/workspace/omegalul/* root@54.66.39.163:~/omegalul"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                // Execute the build Ansible playbook
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/omegalul/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                // Execute the deployment Ansible playbook
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/omegalul/playbooks/deploy.yaml'
            }    
        } 
    }
}
