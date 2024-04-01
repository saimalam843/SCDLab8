pipeline {

    agent any

    
    stages {
         stage('build') {
          steps {
              sh 'npm install'
            }
          }
        
        stage('Docker Comopse Up') {
            steps {
               
                    sh "docker compose up"
                
            }
        }
         stage('kill') {
            steps {
               
                    sh "docker compose down"
                
            }
        }
    }
}