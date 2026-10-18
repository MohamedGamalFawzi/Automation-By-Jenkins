pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/MohamedGamalFawzi/Automation-By-Jenkins.git'
            }
        }
        stage('Verify Docker Inside Jenkins') {
            steps {
                sh 'docker --version'
                sh 'docker ps'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t mogamalfawzy/nginx-lab:v1.$BUILD_NUMBER .'
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push mogamalfawzy/nginx-lab:v1.$BUILD_NUMBER'
                }
            }
        }
    }
}
