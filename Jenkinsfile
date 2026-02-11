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
                sshagent(credentials: ['web-server-ssh']) {
                    sh '''
                    scp -o StrictHostKeyChecking=no -r page1 ubuntu@172.31.29.231:/var/www/
                    scp -o StrictHostKeyChecking=no -r page2 ubuntu@172.31.29.231:/var/www/

                    ssh -o StrictHostKeyChecking=no ubuntu@172.31.29.231 "
                        sudo chown -R www-data:www-data /var/www/page1;
                        sudo chown -R www-data:www-data /var/www/page2;
                        sudo systemctl restart nginx
                    "
                    '''
                }
            }
        }
    }
}
