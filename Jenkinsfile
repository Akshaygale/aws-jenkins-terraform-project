pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-access-key')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-key')
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Akshaygale/aws-jenkins-terraform-project.git'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init infra/'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan -out=infra/tfplan infra/'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve infra/'
            }
        }
    }
}
