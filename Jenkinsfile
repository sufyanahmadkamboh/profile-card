pipeline {
  agent any

  environment {
    TARGET_HOST = '54.151.134.119'
  }

  stages {
    stage('Remote sanity check') {
      steps {
        withCredentials([sshUserPrivateKey(credentialsId: 'server-base',
                                          keyFileVariable: 'SSH_KEY',
                                          usernameVariable: 'SSH_USER')]) {
          sh """
            chmod 600 "$SSH_KEY"
            ssh -i "$SSH_KEY" -o StrictHostKeyChecking=no "$SSH_USER"@"$TARGET_HOST" 'whoami; pwd'
          """
        }
      }
    }
  }
}
