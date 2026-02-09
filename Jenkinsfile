pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code already checked out by Jenkins'
            }
        }

        stage('Deploy to Web Server') {
            steps {
                sshagent(['web-server-ssh']) {
                    sh '''
                      scp index.html ubuntu@172.31.27.91:/var/www/html/
                    '''
                }
            }
        }
    }
}
