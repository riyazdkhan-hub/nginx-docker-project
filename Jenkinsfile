pipeline {
 agent any

 stages {

  stage('Clone Repo') {
   steps {
    git 'https://github.com/riyazdkhan-hub/nginx-docker-project.git'
   }
  }

  stage('Build Docker Image') {
   steps {
    sh 'docker build -t myapp .'
   }
  }

  stage('Stop Old Container') {
   steps {
    sh 'docker stop mycontainer || true'
    sh 'docker rm mycontainer || true'
   }
  }

  stage('Run Container') {
   steps {
    sh 'docker run -d -p 5002:80 --name mycontainer myapp'
   }
  }

 }
}
