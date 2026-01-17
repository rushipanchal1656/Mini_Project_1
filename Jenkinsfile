pipeline {
    agent any

    stages {
        stage('Check Workspace') {
            steps {
                sh 'pwd'
                sh 'ls -l'
            }
        }

        stage('Docker Access Check') {
            steps {
                sh 'docker version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t html-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f html-container || true
                docker run -d -p 80:80 --name html-container html-app
                '''
            }
        }
    }
}
