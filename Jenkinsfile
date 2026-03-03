@Library("shared") _
pipeline {
    agent { label 'vinod'}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/harshjani02/django-notes-app.git","main")
                }
            }
            
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","harshh02")
                }
            }
        }
        stage("Test"){
            steps{
                echo "this is testing the code"
            }
        }
        stage("push to dockerhub"){
            steps{
                script{
                    docker_push("notes-app","latest")
                }
    }
}
        stage("Deploy"){
            steps{
                echo "This is deplying the code"
               // sh "docker run -d -p 8000:8000 notes-app:latest"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
