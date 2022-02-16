pipeline {
  environment {
    imagename = "apache/lsluserd"
    registryCredential = 'dockerhub'
    dockerImage = ''
    DOCKERHUB_CREDENTIALS$ = credentials('dockerhub')
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
          sh 'docker build -t apache/lsluserd:img1 .'
          dockerImage = docker.build imagename
        }
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login  -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push('latest')

          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $imagename:$BUILD_NUMBER"
         sh "docker rmi $imagename:latest"

      }
    }
  }
}
