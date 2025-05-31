pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-node-app .'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests (dummy)'
                bat 'echo Tests Passed!'
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
