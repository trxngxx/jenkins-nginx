pipeline{
  agent none
  stages{
    stage('Init'){
      agent any
      steps{
        sh 'mvn init'
      }       
    }
    stage('Testing'){
      agent any
      steps{
        sh 'echo Testing Done'
      }
    }
    stage('Package'){
      agent any
      steps{
        sh 'mvn package'
      }
    }
    stage('Deploy'){
      agent any
      steps{
        sh label: '', script: '''rm -rf Dockerimage
mkdir Dockerimage
cd Dockerimage
vi index.html
cat <<EOT>>index.html
<!DOCTYPE html>
<html>
   <head>
      <title>Nginx web</title>
   </head>
   <body>
       <h1>xin chao</h1>
       <h2> test1 </h2>
    </body>
</html>
EOT
mkdir html
mv index.html ./html/
cd Dockerimage
touch Dockerfile
cat <<EOT>>Dokerfile
FROM nginx:latest
COPY ./html/* /usr/share/nginx/html/
EXPOSE 80
EOT
sudo docker build -t nginxweb:latest .
sudo docker run -d --name nginxweb -p 8081:80 -v nginx_web:/usr/share/nginx/html/ nginxweb
      }
    }
  }
}
