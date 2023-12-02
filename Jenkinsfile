
pipeline {
  agent any
  
  stages{
    stage("Maven Build"){
      steps{
        sh "mvn clean package"
      }
    }
    stage("Nexus"){
      steps{
        nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/myweb-0.0.2.war', type: 'war']], credentialsId: 'nexus3', groupId: 'in.javahome', nexusUrl: '172.31.35.232:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'my-app-release', version: '0.0.2'
      }
    }
  }
}
