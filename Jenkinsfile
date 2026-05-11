pipeline {

    agent any

    stages {

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Images') {
            steps {
                bat 'docker compose build'
            }
        }

        stage('Deploy Containers') {
            steps {
                bat '''
                       docker compose down
                       docker compose up -d
                      '''
            }
        }

        stage('Verify Running Containers') {
            steps {
                bat 'docker ps'
            }
        }
    }

    post {

        success {
            echo 'Deployment Successful'
        }

        failure {
            echo 'Deployment Failed'
        }
    }
}
