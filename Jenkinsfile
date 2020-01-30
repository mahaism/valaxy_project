pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
                git credentialsId: 'github', url: 'https://github.com/mahaism/valaxy_project.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                //sh "mv target/*.war target/webapp.war"
            }
        }
        
        }
    }
}
