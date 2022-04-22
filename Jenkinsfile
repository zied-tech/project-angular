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
                    sh "perms=$(sudo -l); echo $(whoami); echo $perms" # getting current user and its sudo permissions
                    sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }

        }
	
        }
}
