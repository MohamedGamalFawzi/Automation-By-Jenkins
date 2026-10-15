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
                sh 'docker build -t mogamalfawzy/nginx-lab:$BUILD_NUMBER .'
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push mogamalfawzy/nginx-lab:$BUILD_NUMBER'
                }
            }
        }
    }
}
