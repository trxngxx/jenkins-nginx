pipeline {
  
  agent any
  stages{
    stage('Build Image'){
        when {
          branch 'main'
         }
        agent {
          node {
            label 'test'
            customWorkspace '/var/jenkins_home/workspace/nginx'
          }
         }
      steps {
        sh 'sudo apt-get update && sudo apt-get install -y nginx'
      }
    }

    
            stage('Deploy') {
              when {
             branch 'main'
            }
      agent {
        node {
          label 'test'
          customWorkspace '/var/jenkins_home/workspace/nginx'
        }
         }
            steps {
                sh 'sudo cp /var/lib/jenkins/workspace/my-job/index.html /var/www/html/'
                sh 'sudo cp /var/lib/jenkins/workspace/my-job/nginx.conf /etc/nginx/nginx.conf'
                sh 'sudo systemctl restart nginx'
            }
        }
    }
 }
