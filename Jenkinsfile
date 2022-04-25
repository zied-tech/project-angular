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
<<<<<<< HEAD
                 stage('Build') {
                 steps{
                 script{
                    sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
=======
    stage('Build') {
            steps{
                script{
                    sh "npm install; ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
>>>>>>> f9b001c83b406b5e690674e3f886007502b846ad
                }
            }

        }
	
        }
}
