pipeline {
    agent any

    stages {

        stage('Checkout GIT Web-App-CiCD') {
            steps {
                git 'https://github.com/Velmaniraja/web-app-cicd.git'

            }
        }

        stage('Build latest Image') {
            steps {
                sh 'docker build -t simple-web-app:latest .'
            }
        }

        stage('Stop running container') {
            steps {
                sh '''
                docker stop simple-web-app || true
                docker rm simple-web-app || true
                '''
            }
        }

        stage('Run or Deploy latest container to instance') {
            steps {
                sh 'docker run -d -p 5000:5000 --name simple-web-app simple-web-app:latest'
            }
        }
    }
}