pipeline {
    agent any

    environment {
        ANSIBLE_PLAYBOOK = 'playbook.yaml'  // Playbook name
        ANSIBLE_INVENTORY = 'localhost,'    // Using localhost as inventory
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the repository
                git url: 'https://github.com/vijaysarangapani/sarangapani.git', branch: 'infra-works'
            }
        }

        stage('Validate Files') {
            steps {
                script {
                    // List files in the workspace to ensure the playbook is there
                    sh 'ls -al'
                }
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                script {
                    // Run the Ansible playbook using Ansible plugin
                    ansiblePlaybook(
                        playbook: "${ANSIBLE_PLAYBOOK}",
                        inventory: "${ANSIBLE_INVENTORY}"
                    )
                }
            }
        }
    }

    post {
        success {
            echo 'Application stopped successfully!'
        }
        failure {
            echo 'Application failed to stop.'
        }
    }
}
