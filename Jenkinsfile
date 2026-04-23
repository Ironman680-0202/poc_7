pipeline {
    agent any
 
    environment {
        IMAGE_NAME = "myapp"
    }
 
    stages {
 
        stage('Clone Repo') {
            steps {
                git 'https://github.com/YOUR_USERNAME/POC_1.git'
            }
        }
 
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }
 
        stage('Deploy via Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml -i ansible/inventory'
            }
        }
    }
}