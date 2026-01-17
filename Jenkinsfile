pipeline {
    agent any

    stages {
        stage('Docker Info') {
            steps {
                sh 'docker info'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t html-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f html-container || true
                docker run -d -p 80:80 --name html-container html-app
                '''
            }
        }
    }
}
