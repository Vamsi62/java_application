pipeline {
  
    agent none
    stages {
        stage('Build') { 
            agent any
             steps {
                sh 'mvn install'
              }
            }
       
       stage ('dockerization') {
           agent any
            steps{
              sh 'docker build -t vamsi62/myrepo1 .'
                }
       }
       stage('Deploy Image') {
           agent any
          steps{
          
              withDockerRegistry([ credentialsId: "docker-hub", url: "" ])
               {
                 sh 'docker push vamsi62/myrepo1'
               }
    
            }
        }         
    }      
}
