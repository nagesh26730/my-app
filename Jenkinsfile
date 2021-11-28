@Library('app-libs') _
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
                    tomcatDeploy("172.31.26.51","tomcat-pipeline-dev","myweb")
                    
                }
            }
        }
     post {
          always {
            cleanWs()
          }
          }
    
}
