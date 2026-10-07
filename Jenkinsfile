pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Kubernetes manifests...'
                sh 'test -f deployment.yaml'
                sh 'test -f service.yaml'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo 'Deploying application to Minikube...'
                sh 'minikube kubectl -- apply -f deployment.yaml'
                sh 'minikube kubectl -- apply -f service.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'minikube kubectl -- get deployments'
                sh 'minikube kubectl -- get pods'
                sh 'minikube kubectl -- get services'
            }
        }
    }

    post {
        success {
            echo 'Kubernetes deployment completed successfully.'
        }

        failure {
            echo 'Kubernetes deployment failed.'
        }
    }
}
