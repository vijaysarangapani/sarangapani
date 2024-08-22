pipeline {
    agent any

    environment {
        ANSIBLE_PLAYBOOK = 'stop_and_check_with_logging.yml'
        ANSIBLE_INVENTORY = 'localhost,'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://your-git-repo-url.git', branch: 'main'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                script {
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

