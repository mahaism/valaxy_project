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
        stage("deploy-dev"){
            steps{
                sshagent(['tomcat-server']) {
                sh """
                    scp -o StrictHostKeyChecking=no target/webapp.war  ec2-user@52.66.22.121:/opt/tomcat/webapps/
                    
                    ssh ec2-user@52.66.22.121 /opt/tomcat/bin/shutdown.sh
                    
                    ssh ec2-user@52.66.22.121 /opt/tomcat/bin/startup.sh
                
                """
            }
            
            }
        }
    }
}
