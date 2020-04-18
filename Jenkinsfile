pipeline {
    // runs on any 'agent' (can either be a master or slave) that has ansible installed
    agent any
    stages {
        stage('Checkout') {
            steps {
                script {
                    git 'https://github.com/colinbut/microservice-aws-ec2-docker-deployment.git/'
                }
            }
        }
        stage('Execute Ansible Playbook') {
            steps {
                // Needs Ansi Plugin that enables colourful printing on Console Log output
                ansiColor('xterm') {
                    ansiblePlaybook(
                        playbook: 'deploy.yml', 
                        inventory: 'hosts', 
                        extraVars: [
                                VERSION: '1.0.0-SNAPSHOT', 
                                HOST_PORT: 3000, 
                                CONTAINER_PORT: 3000, 
                                MICROSERVICE_NAME: 'microservice-nodejs'
                                ], 
                        installation: 'ansible', 
                        credentialsId: 'ssh-to-server', 
                        disableHostKeyChecking: true,
                        colorized: true, 
                    )
                }
                
            }
        }
    }
}