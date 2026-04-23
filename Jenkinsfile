pipeline {
    agent any
 
    environment {
        IMAGE_NAME = "myapp"
    }
 
    stages {
 
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Ironman680-0202/poc_7.git'
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