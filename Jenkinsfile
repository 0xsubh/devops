pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Check out your code from a Git repository without credentials
                git(url: 'https://github.com/0xsubh/devops.git', branch: 'main')
            }
        }
        stage('Install MongoDB') {
            steps {
                script {
                    // Run the Ansible playbook to install MongoDB with sudo permissions
                    sh '/opt/homebrew/bin/ansible-playbook -i localhost, -c local install_mongodb.yml -u subhamsharma --become --become-user=root'
                }
            }
        }
        stage('Check MongoDB Installation') {
            steps {
                script {
                    def result = sh(script: 'mongod --version', returnStatus: true)
                    if (result == 0) {
                        echo "MongoDB is installed."
                    } else {
                        error "MongoDB is not installed."
                    }
                }
            }
        }
    }
}
s