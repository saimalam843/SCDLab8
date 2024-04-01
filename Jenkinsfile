pipeline {
    agent any

    environment {
        // Define environment variables if needed
        // REACT_APP_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checks out the repository from GitHub
                checkout scm
            }
        }

        stage('Dependency Installation') {
            steps {
                // Assuming there's a package.json at the root directory of your project
                script {
                    // Install dependencies for Node.js (React)
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                // Build the React application
                script {
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            steps {
                // Run the React application tests
                script {
                    sh 'npm test'
                }
            }
        }

        stage('Containerize') {
            steps {
                // Build Docker images and run containers using Docker Compose
                // Assuming you have a Dockerfile at the root and a docker-compose.yml
                script {
                    // Build the Docker image
                    sh 'docker build -t react-bank-app .'

                    // Assuming the Docker Compose file orchestrates your React app and any other services
                    sh 'docker-compose up -d'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Any additional deployment steps or scripts
                echo 'Deploying application...'
                // For example, you might have a script to update a server or service
                // sh './deploy.sh'
            }
        }
    }

    post {
        // Define post-build actions
        always {
            echo 'Cleaning up...'
            // Clean up Docker images, containers, or other resources if needed
            // sh 'docker-compose down'
        }

        success {
            echo 'Build and deployment succeeded!'
        }

        failure {
            echo 'Build or deployment failed.'
        }
    }
}
