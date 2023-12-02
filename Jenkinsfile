
pipeline{
   
            stages{
             stage('Mvn Build'){
                steps{
                    sh 'mvn clean package'
                }
            }
        
       stage("Nexus Deploy"){
            steps{
                script{
                    def pomFile = readMavenPom file: 'pom.xml'
                    nexusArtifactUploader artifacts: 
                [[
                artifactId: 'myweb', 
                classifier: '',  
                file: "target/my-app.war",
                type: 'war'
                ]], 
                 credentialsId: 'nexus3', 
                 groupId: 'in.javahome', 
                 nexusUrl: '172.31.71.247:8081',
              }
            }
       }
            }            
}
           
       
