pipeline {
  
  agent any
  stages{
    stage('Build Image'){
        when {
          branch 'main'
         }
        agent {
          
            
            customWorkspace '/root/Dockerimage/'
            
         }
      steps {
        sh "cd /root/Dockerimage && docker build -t nginxweb:latest ."
      }
    }

    stage('Deploy'){
       when {
             branch 'main'
            }
      agent {
       
          
          customWorkspace '/root/Dockerimage/'
            
         }
      steps {
        sh """
        echo "Deploy code"
        """
        }
      }
    }
 }
