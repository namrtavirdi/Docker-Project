pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Docker') {
            steps {
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t leaf-disease-app:latest .'
            }
        }

        stage('List Images') {
            steps {
                bat 'docker images'
            }
        }
    }

    post {
        success {
            echo '======================================='
            echo 'Docker Image Built Successfully!'
            echo '======================================='
        }

        failure {
            echo '======================================='
            echo 'Docker Build Failed!'
            echo '======================================='
        }
    }
}
