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
                echo 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo 'npm test'
            }
        }

        stage('Containerize') {
            steps {
                echo 'docker build -t react-bank-app .'
            }
        }

        stage('Docker Compose Up') {
            steps {
                echo 'docker-compose up -d'
            }
        }

        stage('Clean Up') {
            steps {
                echo 'docker-compose down'
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
            echo 'docker-compose down'
        }
    }
}
