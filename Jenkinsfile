pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git(
                    url: 'https://github.com/0xsubh/devops.git', branch: 'main'
                    
                )
            }
        }
        stage('Install Nginx') {
            steps {
                script {
                    // Run the Ansible playbook to install Nginx
                    sh '''
                        ansible-playbook -i localhost, -c local nginx-install.yml
                    '''
                }
            }
        }
        stage('Check Nginx Installation') {
            steps {
                script {
                    def result = sh(script: 'nginx -v', returnStatus: true)
                    if (result == 0) {
                        echo "Nginx is installed."
                    } else {
                        error "Nginx is not installed."
                    }
                }
            }
        }
    }
}
