pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[credentialsId: '57eae3e3-5ac5-4be8-bcc1-709aee3f0f77',
                            url: 'https://github.com/MarwanBenAbdelkader/my-app.git']]])
                }
            }
        }
    }
}
