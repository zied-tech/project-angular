pipeline { 
	
	agent any 
	stages { 
	    
		stage('pull') {
		steps {
            script {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                userRemoteConfigs: [[
                    credentialsID: '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',
                    url: 'https://github.com/zied-tech/project-angular.git'
                ]]]                  
                )
            } 
		}
		}
    stage('Build') {
            steps{
                script{
                    sh "npm install; ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }

        }
        stage('Docker') {
            steps{
                script{
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                }
            }

        }
	
        }
}
