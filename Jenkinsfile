pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                echo 'Code cloned from GitHub'
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
