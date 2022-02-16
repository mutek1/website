pipeline {
    environment {
    imagename = "lsluserd/img2:gitimg"
    registryCredential = 'dockerhub'
    dockerhub = credentials('dockerhub')
    dockerImage = ''
    }
  agent any
  stages {
      when {
          branch "prod"
      }
      steps {
          sh 'docker build -t lsluserd/img2:gitimg .'
      }
  }
}
      
