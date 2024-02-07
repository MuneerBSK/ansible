pipeline {
    agent { label 'ws' }
    environment {
        SSH_CREDENTIALS = credentials('SSH_CRED')
    }
    stages {
        stage("performing the ansible dry run") {
            steps{
                sh "env"
                sh "ansible-playbook robot-dryrun.yaml -e COMPONENT=mongodb -e ansible_user=${SSH_CREDENTIALS_USER} -e ansible_password=${SSH_CREDENTIAL} -e ENV=qa"
            }
        }
    }
}