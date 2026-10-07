pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'test -f index.html'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application...'
                sh 'grep -q "DevOps CI/CD Pipeline" index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'mkdir -p /tmp/devops-deployment'
                sh 'cp index.html /tmp/devops-deployment/index.html'
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully.'
        }

        failure {
            echo 'Pipeline failed.'
        }
    }
}
