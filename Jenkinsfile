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
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("deploy-dev"){
            steps{
                sshagent(['tomcat-server']) {
                sh """
                    scp -o StrictHostKeyChecking=no target/myweb.war  ec2-user@172.31.11.242:/opt/tomcat/webapps/
                    
                    ssh ec2-user@172.31.11.242 /opt/tomcat/bin/shutdown.sh
                    
                    ssh ec2-user@172.31.11.242 /opt/tomcat/bin/startup.sh
                
                """
            }
            
            }
        }
    }
}
