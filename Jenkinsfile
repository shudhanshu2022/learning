pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'jeniks-deploy'
    }
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/shudhanshu2022/learning.git'
            }
        }
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test || true' // Optional
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }
        stage('Run App') {
            steps {
                sh 'docker stop node-app || true && docker rm node-app || true'
                sh 'docker run -d -p 3000:3000 --name node-app $DOCKER_IMAGE'
            }
        }
    }
}


