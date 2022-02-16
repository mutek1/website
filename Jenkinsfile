pipeline {
  agent any 
   tools {
    maven 'maven'
    jdk 'Java'
  }
  environment {
    imagename = "lsluserd/img1:gitimg"
    registryCredential = 'dockerhub''
    dockerhub = credentials('dockerhub')
    dockerImage = ''
    }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
           dockerImage = docker.build imagename
           sh 'docker build -t lsluserd/img2:gitimg .'
        }
      }
    }
    stage('Login') {
      steps {
        sh 'docker login -u lsluserd'
      }
    }
    
   
  }
}
