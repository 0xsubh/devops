pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git(url: 'https://github.com/0xsubh/devops.git', branch: 'main')
            }
        }
        stage('Install MongoDB') {
            steps {
                script {
                    // Use expect to provide the password to sudo
                    sh '''
                        /usr/bin/expect <<EOD
                        spawn sudo /opt/homebrew/bin/ansible-playbook -i localhost, -c local install_mongodb.yml -u subhamsharma --become --become-user=root
                        expect "Password:"
                        send "subham\r"
                        expect eof
                        EOD
                    '''
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
