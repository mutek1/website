pipeline {
  environment {
    imagename = "apache/lsluserd"
    registryCredential = 'dockerhub'
    dockerImage = ''
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
        docker login -u lsluserd
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
