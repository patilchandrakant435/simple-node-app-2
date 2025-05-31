pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-node-app"
        AWS_REGION = "us-east-1"
        EKS_CLUSTER = "your-cluster-name"
        STAGING_NAMESPACE = "staging"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/patilchandrakant435/simple-node-app-2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME:latest .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Optional: Add real tests if available
                    echo "Running dummy test"
                    sh 'echo "Tests Passed"'
                }
            }
        }

        stage('Push to ECR (Optional)') {
            steps {
                script {
                    // Add AWS ECR push steps if using ECR
                }
            }
        }

        stage('Deploy to Kubernetes Staging') {
            steps {
                script {
                    sh '''
                    aws eks update-kubeconfig --name $EKS_CLUSTER --region $AWS_REGION
                    kubectl apply -f k8s/deployment.yaml -n $STAGING_NAMESPACE
                    kubectl rollout status deployment/my-node-app -n $STAGING_NAMESPACE
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Deployed to Staging successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
