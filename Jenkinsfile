pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Dependency Installation') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Containerize') {
            steps {
                sh 'docker build -t react-bank-app .'
            }
        }

        stage('Docker Compose Up') {
            steps {
                sh 'docker-compose up -d'
            }
        }

        stage('Clean Up') {
            steps {
                sh 'docker-compose down'
            }
        }
    }

    post {
        always {
            echo 'The pipeline has finished executing.'
        }

        success {
            echo 'The build was successful!'
        }

        failure {
            echo 'The build failed.'
        }

        cleanup {
            sh 'docker-compose down'
        }
    }
}
