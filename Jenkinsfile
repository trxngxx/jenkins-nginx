pipeline {
  
  agent none
  stages{
    stage('Build Image'){
        when {
          branch 'main'
         }
        agent {
          node {
            customWorkspace '/home/ngo1/Dockerimage/'
             }
         }
      steps {
        sh "cd /home/ngo1/Dockerimage && docker build -t nginxweb:latest ."
      }
    }

    stage('Deploy'){
       when {
             branch 'main'
            }
      agent {
        node {
          customWorkspace '/home/ngo1/Dockerimage/'
            }
         }
      steps {
        sh """
        echo "Deploy code"
        """
        }
      }
    }
  }
}
