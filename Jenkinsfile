node {
   stage('Example') {
		sh './set-up.sh'
        try {
            sh "sudo docker kill $(docker ps -q)"
            sh "docker rm $(docker ps -a -q)"
            sh "docker rmi $(docker images -q)"

        } catch (err) {
            echo err.getMessage()
            echo "Error detected, but we will continue."
        }
        ...continue with other code...
     }
}
