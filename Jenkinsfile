pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/akumariit6/Pythonapp.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh "make image"     // all commands are written in makefile
            }
        }
        stage('Push Docker Image') {
            steps {
                sh "make push"
            }
        }
        stage('Docker deploy') {
            steps {
                sh "docker images"
                sh "docker run -d -p 5000:5000 akumariit6/python-demoapp:latest"
            }
        }
    }
}

