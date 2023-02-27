pipeline {
    agent any

    stages {
        stage('Copy website') {
            steps {
                cleanWs()
                echo '[INFO] Cloning Repository' 
                sh 'git clone --depth 1 --single-branch https://github.com/ysabelandreii/Sample-Website.git -b sample-website'
                
            }
        }

        stage('Deploy to EC2 instance') {
            steps {
                echo '[INFO] Deploying to AWS'
                // sh 'scp -r web_app user@ip_add:/var/www/html'
            }
        }

        stage('Send Slack notification') {
            steps {
                echo '[INFO] Sending Notifications'
            }
        }
    }
}
