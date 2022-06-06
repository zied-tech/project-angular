pipeline {
    agent any
    stages {
        stage('pull from git') {
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
        stage('Build angular app') {
            steps {
                script {
                    sh 'ansible-playbook ansible/build.yml -i ansible/inventory/host.yml'
                }
            }
        }
        stage('build and run image') {
            steps {
                script {
                    sh 'ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml'
                }
            }
        }
        stage('Upload image to Docker Hub') {
            steps {
                script {
                    sh 'ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml'
                }
            }
        }
        stage('email notifiication'){
    steps {
          emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
          recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
          subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
      }
    }
    }
}
