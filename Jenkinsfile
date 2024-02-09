pipeline {
    agent { label 'ws' }
    environment {
        SSH_CREDENTIALS = credentials('SSH_CRED')
    }
    stages {

        stage('testing the tags') {
            when {expression { env.TAG_NAME == ".*"} }
            steps {
                sh "env"
            }

        }
        stage('Performing Lint Check') {
            when { 
                branch pattern: "feature -.* ", comparator: "REGEXP"
            }
            steps {
                sh "env"
                sh "echo This step should run against non-main branches only"
                sh "echo PERFORMING LINT CHECKS"
                // Add your lint check command here
            }
        }
        
        stage("Performing the Ansible dry run") {
            steps {
                sh "env"
                sh "ansible-playbook robot-dryrun.yaml -e COMPONENT=mongodb -e ansible_user=${SSH_CREDENTIALS_USR} -e ansible_password=${SSH_CREDENTIALS_PSW} -e ENV=qa"
            }
        }
        
        stage('Promotion To Prod Branch') {
            when {
                expression { env.BRANCH_NAME == 'main' }
            }
            steps {
                sh "env"
                sh "echo printing"
                sh "echo main - PROMOTING To PRODUCTION"
            }
        }
    }       
    // Add post actions or other configurations if needed
}
