pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/patilchandrakant435/simple-node-app-2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-node-app .'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests (dummy)'
                sh 'echo "Tests Passed!"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'This is the deploy stage (not implemented yet).'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
