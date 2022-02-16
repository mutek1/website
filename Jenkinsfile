pipeline {
    agent any 
    environment {
    imagename = "lsluserd/img2:gitimg"
    registryCredential = 'dockerhub'
    dockerhub = credentials('dockerhub')
    dockerImage = ''
    }
   stage('build image') {
      when {
          branch "test"
      }
      steps {
          sh 'docker build -t lsluserd/img2:gitimg .'
      }
  }
}
      
