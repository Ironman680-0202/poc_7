pipeline {
    agent any
 
    environment {
        IMAGE_NAME = "myapp"
    }
 
    stages {
 
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Ironman680-0202/poc_7.git'
            }
        }
 
        stage('Prepare App') {
            steps {
                sh 'echo Preparing application...'
            }
        }
 
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }
 
        stage('Tag Image') {
            steps {
                sh 'docker tag $IMAGE_NAME $IMAGE_NAME:latest'
            }
        }
 
        stage('Deploy via Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml -i ansible/inventory'
            }
        }
 
        stage('Verify Deployment') {
            steps {
                sh 'curl -I http://localhost || true'
            }
        }
    }
}