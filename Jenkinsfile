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
          sh 'sudo docker system prune --force --all --volumes'
          sh 'sudo docker run -itd --name master -p 91:80 lsluserd/img1:gitimg'
          sh 'docker build -t lsluserd/img1:gitimg .'
          dockerImage = docker.build imagename
        }
      }
    }
    stage('Login') {
      steps {
        sh 'docker login -u lsluserd'
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
