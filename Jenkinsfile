pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-token',
                    url: 'https://github.com/richiee3/devops-cicd-assignment.git'
            }
        }

        stage('Deploy to Web Server') {
            steps {
                sshagent(credentials: ['web-server-ssh']) {
                    sh '''
                        ssh -o StrictHostKeyChecking=no ubuntu@18.222.135.208 \
                        "sudo rm -rf /var/www/html/*"
                        
                        scp -o StrictHostKeyChecking=no index.html \
                        ubuntu@18.222.135.208:/var/www/html/
                    '''
                }
            }
        }
    }
}
