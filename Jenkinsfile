pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout your code from a Git repository if needed
            }
        }
        stage('Run Ansible Playbook') {
            steps {
                script {
                    ansiblePlaybook(
                        playbook: 'install_mongodb.yml',
                        inventory: 'localhost,',
                        installation: 'Default'
                    )
                }
            }
        }
    }
}

