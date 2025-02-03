 @Library("sharedLibrary") _
 pipeline {
     agent { label "vijay" }
     stages{
         stage("Hello from github"){
             steps{
                 script{
                     hello()   
                 }
             }
         }
         stage("Clone Code"){
             steps{
                 script{
                     cloneCode("https://github.com/LondheShubham153/django-notes-app.git","main")
                 }
             }
         }
         stage("Build and Test"){
             steps{
                 script{
                     docker_build("django-note-app","latest","181190101033")
                 }
             }
         }
         stage("Push to Docker Hub"){
             steps{
                 echo "Docker Hub will push the image to docker hub"
                 script{
                     docker_push("django-note-app","latest","181190101033")
                    }
                 }
             }
         stage("Deploy"){
             steps{
                 echo "Docker Hub will deploy the image"
                 sh "docker-compose down && docker-compose up -d"
             }
         }
     }
 }
