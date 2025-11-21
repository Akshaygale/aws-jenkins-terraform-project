pipeline {
  agent any

  environment {
    AWS_CREDS = credentials('aws-creds')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/yourusername/aws-jenkins-terraform-project.git'
      }
    }

    stage('Terraform Init') {
      steps {
        sh 'terraform init infra/'
      }
    }

    stage('Terraform Apply') {
      steps {
        sh 'terraform apply -auto-approve infra/'
      }
    }
  }
}

