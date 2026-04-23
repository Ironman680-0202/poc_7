pipeline {
    agent any

    stages {

        stage('Prepare Application') {
            steps {
                sh '''
                echo "Preparing application"
                ls -l
                test -f Dockerfile
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build --no-cache -t myapp:latest .'
            }
        }

        stage('Deploy via Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml -i ansible/inventory'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'curl -f http://localhost:5000'
            }
        }
    }
}
