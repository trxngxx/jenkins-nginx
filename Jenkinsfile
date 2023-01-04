pipeline {
  
  agent none
  stages{
    stage('Build Image'){
        when {
          branch 'main'
         }
        agent {
          node {
            label 'ubuntu'
            customWorkspace '/root/Dockerimage/'
          }
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
        node {
          label 'ubuntu'
          customWorkspace '/root/Dockerimage/'
        }
         }
      steps {
        sh """
        echo "Deploy code" && docker run -d --name nginxweb -p 8081:80 -v nginx_web:/usr/share/nginx/html nginxweb
        """
        }
      }
    }
 }
