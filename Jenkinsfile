pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Deploy to Web Server') {
    steps {
        sshagent(['web-server-ssh']) {
            sh '''
            ssh -o StrictHostKeyChecking=no ubuntu@172.31.29.231 "rm -rf /var/www/page1 /var/www/page2"
            scp -o StrictHostKeyChecking=no -r page1 page2 ubuntu@172.31.29.231:/var/www/
            '''
        }
    }
}

    }
}
