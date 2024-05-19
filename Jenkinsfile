pipeline {
    agent {
        label 'ansible'
    }
environment {
  AWS_EC2_PRIVATE_KEY=credentials ('ec2-private-key')
}
    stages {
        stage('checkout code') {
            steps {
                git branch: 'main', url: 'https://github.com/pinnacloud/jenkins-ansible-static-inv.git'
            }
        }
        stage('Run Playbooks') {
            steps {
                sh "ansible-playbook -i inventory/pinnacloud.hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/installtomcat9.yaml --ssh-common-args='-o StrictHostKeyChecking=no'"
            }
        }
        
    }
}
