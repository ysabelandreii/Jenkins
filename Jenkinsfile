pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                // Clone the Git repository containing the sample webpage
                git 'https://github.com/example/sample-webpage.git'
            }
        }

        stage('Deploy to AWS') {
            steps {
                // Use AWS CLI to copy the files to an S3 bucket
                withAWS(region: 'us-west-2', credentials: 'aws-credentials') {
                    sh 'aws s3 cp --recursive ./ s3://my-bucket-name/'
                }
            }
        }
    }

    post {
        // Notify a Slack channel about the status of the deployment
        success {
            slackSend(channel: '#deployments', message: 'Deployment successful!')
        }
        failure {
            slackSend(channel: '#deployments', message: 'Deployment failed!')
        }
    }
}
