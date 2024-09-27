pipeline {
    agent any

    stages {
        stage('Initialize Terraform') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Apply Terraform') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }

        stage('Wait for Deployment') {
            steps {
                sleep 10
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh 'ansible-playbook -i /tmp/inv -u ec2-kumaruser -b --become-method sudo web.yaml'
            }
        }
    }
}
