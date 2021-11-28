pipeline{
    
    agent any
        stages{
            stage('Git SCM'){
                steps{
                     git branch: 'dev', url: 'https://github.com/nagesh26730/my-app'
                }
            }
            stage('Maven Build'){
                steps{
                     sh 'mvn clean package'
                     sh 'mv target/myweb*.war target/myweb.war'
                }
            }
            stage('Deploy war file to the Development'){
                steps{
                    sshagent(['tomcat-pipeline-dev']) {
                      sh "scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.26.51:/opt/tomcat/webapps/"
                      sh "ssh ec2-user@172.31.26.51 /opt/tomcat/bin/shutdown.sh"
                      sh "ssh ec2-user@172.31.26.51 /opt/tomcat/bin/startup.sh"
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
