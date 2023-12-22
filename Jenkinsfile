
pipeline {
  agent any
  
  stages{
     stage("SCM"){
      steps{
        git 'https://github.com/nagesh26730/my-app'
      }
    }
    stage("Maven Build"){
      steps{
        sh "mvn clean package"
      }
    }
    
  }
}
