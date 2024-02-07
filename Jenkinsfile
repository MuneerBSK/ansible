pipeline {
    agent { label 'ws' }
    environment {
        SSH_CREDENTIALS = credentials('SSH_CRED')
    }
    stages {

        stage('Performing lint checks') {
            steps {
                sh "env"
                sh "echo This step should run against non-main branches only"
                sh "echo PERFORMING LINT CHECKS"
            }
        }

        stage("performing the ansible dry run") {
            steps{
                sh "env"
                sh "ansible-playbook robot-dryrun.yaml -e COMPONENT=mongodb -e ansible_user=${SSH_CREDENTIALS_USR} -e ansible_password=${SSH_CREDENTIALS_PSW} -e ENV=qa"
            }
        }
    }
}