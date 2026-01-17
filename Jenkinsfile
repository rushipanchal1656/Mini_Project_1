pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Checking out code from GitHub'
                checkout scm
            }
        }

        stage('Verify Workspace') {
            steps {
                sh '''
                echo "Current directory:"
                pwd
                echo "Files in workspace:"
                ls -l
                '''
            }
        }

        stage('Docker Version Check') {
            steps {
                sh 'docker --version'
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

    post {
        success {
            echo '✅ Build and Deployment Successful'
        }
        failure {
            echo '❌ Build Failed'
        }
    }
}
