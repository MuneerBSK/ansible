pipeline {
    agent { label 'ws' }
    environment {
        SSH_CREDENTIALS = credentials('SSH_CRED')
    }
    stages {
        stage("performing the ansible dry run") {
            steps{
                sh "ansible-playbook robot-dryrun.yaml -e COMPONENT=mongodb -e ansible_user=centos -e ansible_password=xyz123 -e ENV=qa"
            }
        }
    }
}