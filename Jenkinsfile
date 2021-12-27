@Library('app-libs') _
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
                
                 tomcatDeploy("172.31.3.50","Tomcat-Development","myweb")
            }
            }
        }
     /*  # stage("Deploy to Tomcat qa"){
            #steps{
              # sshagent(['Tomcat-qa']) {
                #  sh "scp -o StrictHostKeyChecking=no target/myweb*.war ec2-user@172.31.5.166:/opt/tomcat8/webapps/"
                #  sh "ssh ec2-user@172.31.5.166 sudo /opt/tomcat8/bin/shutdown.sh"
                  #sh "ssh ec2-user@172.31.5.166 sudo /opt/tomcat8/bin/startup.sh"
                 # }
           # }
       # }*/
    }
    
       post {
          always {
          cleanWs()
         }
}

