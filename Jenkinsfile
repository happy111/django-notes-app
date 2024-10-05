
@Library("Shared") _

pipeline {
    agent {label 'umesh'}

    environment {
        DOCKER_CREDENTIALS_ID = 'docker-cred'  // Replace with your actual credentials ID
    }


    stages {
        
        stage('Hello') {
            steps {
               script{
                   hello()
               }
            }
        }
        
        stage('Checkout') {
            steps {
                
                script{
                    
                    clone("main","https://github.com/happy111/django-notes-app.git")
                }
                
                
            }
        }
        
        stage('Docker build') {
            steps {
           
    
              docker_build("notes-app","latest","umeshsamal12345")

            }
        }
        
        stage('Docker Login') {
            steps {
                 script {
                docker_login("notes-app","latest","umeshsamal12345")

                }
            }
        }
        
        stage('Docker run') {
            steps {
                echo "Helll"
            //   sh 'docker run -d -p 8001:8000  notes-app:latest '
            }
        }
        stage('Docker compose') {
            steps {
               sh 'docker-compose down'
               sh 'docker-compose up -d'
            }
        }
        
        
        
    }
}
