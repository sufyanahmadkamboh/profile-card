pipeline {
  agent any

  environment {
    TARGET_HOST = '54.151.134.119'   // or hostname
    SSH_USER    = 'ubuntu'           // whatever user matches the key
  }

  stages {
    stage('Remote sanity check') {
      steps {
        sshagent(credentials: ['server-base']) {
          sh """
            ssh -o StrictHostKeyChecking=no ubuntu@${TARGET_HOST} 'whoami; pwd'
          """
        }
      }
    }
  }
}
