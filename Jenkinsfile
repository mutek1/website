pipeline {
    environment {
    imagename = "lsluserd/img2:gitimg"
    registryCredential = 'dockerhub'
    dockerhub = credentials('dockerhub')
    dockerImage = ''
    }
  agent any
  stages {
    stage('Building image') {
      steps{
           dockerImage = docker.build imagename           
        }
    }
   }
}
