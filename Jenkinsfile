pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/piyoush007/ci-cd-demo.git'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn clean test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t ci-cd-demo:latest .'
            }
        }

        stage('Docker Run') {
            steps {
                bat 'docker stop ci-cd-demo || exit /b 0'
                bat 'docker rm ci-cd-demo || exit /b 0'
                bat 'docker run -d --name ci-cd-demo -p 8080:8080 ci-cd-demo:latest'
            }
        }

        stage('Verify') {
            steps {
                bat 'curl http://localhost:8080'
            }
        }
    }
}
