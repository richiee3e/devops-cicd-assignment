stage('Deploy to Web Server') {
    steps {
        sshagent(['web-server-ssh']) {
            sh '''
              scp -o StrictHostKeyChecking=no \
                  -o UserKnownHostsFile=/dev/null \
                  index.html ubuntu@172.31.27.91:/tmp/

              ssh -o StrictHostKeyChecking=no ubuntu@172.31.27.91 \
                  "sudo mv /tmp/index.html /var/www/html/index.html"
            '''
        }
    }
}
