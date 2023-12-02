
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
        nexusArtifactUploader artifacts: [[artifactId: 'myweb',
                                           classifier: '', 
                                           file: '/target/my-app.war',
                                           type: 'war']],
           credentialsId: 'nexus', 
           groupId: 'in.javahome',
           nexusUrl: '172.31.71.247:8081',
           nexusVersion: 'nexus3', 
           protocol: 'http',
           repository: 'nexusRepoName',
           version: '0.0.1'
      }
    }
  }
}
