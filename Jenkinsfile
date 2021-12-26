pipeline{
    agent any
    stages{
        stage("SCM checkout"){
            steps{
                git credentialsId: '2f0c3c15-e9e2-4b1e-b480-a5de49aa9813', url: 'https://github.com/nagesh26730/my-app'
            }
        }
        stage("Maven Build"){
            steps{
               sh 'mvn clean package'
               sh "mv target/myweb*.war target/myweb.war"
            }
        }
        stage("Deploy to Tomcat Development"){
            steps{
               sshagent(['Tomcat-Development']) {
                  sh "scp -o StrictHostKeyChecking=no target/myweb*.war ec2-user@172.31.3.50:/opt/tomcat8/webapps/"
                  sh "ssh ec2-user@172.31.3.50 sudo /opt/tomcat8/bin/shutdown.sh"
                  sh "ssh ec2-user@172.31.3.50 sudo /opt/tomcat8/bin/startup.sh"
                  }
            }
        }
    }
    
       post {
          always {
          cleanWs()
         }
}
}
