pipeline {
    agent any

    environment {
        IMAGE_NAME = "leaf-disease-app"
        IMAGE_TAG = "latest"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/namrtavirdi/Docker-Project.git'
            }
        }

        stage('Verify Docker') {
            steps {
                bat 'docker --version'
                bat 'docker info'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME%:%IMAGE_TAG% .'
            }
        }

        stage('Show Docker Images') {
            steps {
                bat 'docker images'
            }
        }

    }

    post {
        success {
            echo '================================='
            echo 'Docker Image Built Successfully!'
            echo '================================='
        }

        failure {
            echo '================================='
            echo 'Docker Build Failed!'
            echo '================================='
        }
    }
}
