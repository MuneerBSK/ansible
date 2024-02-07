pipeline {
    agent { label 'ws' }
    stages {
        stage("performing the ansible dry run") {
            steps{
                sh "ansible-playbook robot-dryrun.yaml -e COMPONENT=mongodb -e ansible_user=centos -e ansible_password=xyz123 -e ENV=qa"
            }
        }
    }