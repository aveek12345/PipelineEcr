pipeline {
  
   agent any
    stages {
    stage('Extract from Github') {
      steps {
        script {
          git branch: 'master',  url: 'https://github.com/irwin-tech/docker-pipeline-demo.git'
          }
       }
    }
    
    stage('Docker Build') {
      steps {
        script {
          docker.build('worker')
         
          }
       }
    }
    
/* Mention url of ecr repository within the quotes in docker.withRegistry. The url must begin with https:// */
 stage ('Docker push'){
      steps{
          script{
          docker.withRegistry('', 'ecr:us-east-1:aws creds') {
          docker.image('worker').push('latest')
      }
     

          }
          
  }
  }
    
    }
}
    
