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

       stage('Install') {
             steps{
                script{
                    sh "sudo npm install"
                }
            }
        }



       stage ('Build') {
	
			steps {
			
			sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
	
			     }
	               }

      stage('Docker') {
             steps{
                script{
                    sh "sudo ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml"
                }
            }
        }

     stage('docker_registry') {
             steps{
                script {
                   sh "ansible-playbook Ansible/docker_registry.yml -i Ansible/inventory/host.yml "
                  }
            }
       }

 }

}
