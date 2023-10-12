pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Check out your code from a Git repository without credentials
                git(url: 'https://github.com/0xsubh/devops.git', branch: 'main')
            }
        }
        stage('List Contents') {
            steps {
                script {
                    // List the contents of the 'devops' directory to confirm the presence of the playbook
                    sh 'ls -la devops'
                }
            }
        }
        stage('Install MongoDB') {
            steps {
                script {
                    // Change to the directory where your playbook is located
                    dir('devops') {
                        // Run the Ansible playbook to install MongoDB
                        sh '/opt/homebrew/bin/ansible-playbook -i localhost, -c local install_mongodb.yml'
                    }
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
