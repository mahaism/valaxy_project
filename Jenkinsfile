pipeline {
   agent any
   environment{
      PATH = "/opt/maven/bin:$PATH"
   }
   stages{
      stage{
         git credentialsId: 'github', url: 'https://github.com/mahaism/valaxy_project.git'
      }
   }
   
   stages{
      stage("Maven Build"){
         stepes{
               sh "mvn clean package"
         }
         
      }
      
      stage("deploy-dev"){
      
      }
   
   }



}
