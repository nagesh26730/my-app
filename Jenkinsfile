
pipeline {
  agent any
  
  stages{
     stage("Maven Build"){
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
