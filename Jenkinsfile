pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/mohamed-atef2022/depi-project.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'docker build -t mohamedatef2022/nginx-lab:latest .'
                }
            }
        }
    }
}
