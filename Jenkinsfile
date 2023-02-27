pipeline {
    agent any

    stages {
        stage('Copy website') {
            steps {
                cleanWs()
                echo '[INFO] Cloning Repository'
                sh 'git clone --depth 1 --single-branch https://github.com/ysabelandreii/Sample-Website.git -b sample-website'
                ls 'Sample-Website'
            }
        }

        stage('Deploy to EC2 instance') {
            environment {
                // Customize these environment variables for your EC2 instance
                EC2_IP = '35.160.168.200'
                EC2_USER = 'ec2-user'
                SSH_KEY = credentials('jenkins')
            }
            steps {
                echo '[INFO] Deploying to AWS'
                // Uncomment and customize the following command to deploy the website to your EC2 instance
                // sh "ssh -i ${SSH_KEY} ${EC2_USER}@${EC2_IP} 'cd /var/www/html && rm -rf * && scp -r /path/to/Sample-Website/* .'"
            }
        }

        stage('Send Slack notification') {
            steps {
                echo '[INFO] Sending Notifications'
            }
        }
    }
}

