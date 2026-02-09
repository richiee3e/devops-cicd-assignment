stage('Deploy to Web Server') {
    steps {
        sshagent(['web-server-ssh']) {
            sh '''
              scp -o StrictHostKeyChecking=no index.html ubuntu@172.31.27.91:/var/www/html/
            '''
        }
    }
}
