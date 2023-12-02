
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
                                           file: 'target/myweb-0.0.1.war',
                                           type: 'war']],
           credentialsId: 'nexus', 
           groupId: 'in.javahome',
           nexusUrl: '172.31.71.247:8081',
           nexusVersion: 'nexus3', 
           protocol: 'http',
           repository: 'OSS 3.62.0-01',
           version: '0.0.1'
      }
    }
  }
}
