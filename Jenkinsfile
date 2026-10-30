pipeline {
    agent any

    stages {

        stage('GitHub Checkout') {
            steps {
                checkout scm
                echo 'Code downloaded from GitHub'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'test -f index.html'
                echo 'Build successful'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to Nginx...'
                sh '/opt/deploy.sh "$WORKSPACE"'
            }
        }

        stage('Verify') {
            steps {
                sh 'curl -f http://localhost/'
                echo 'Deployment verified!'
            }
        }
    }
}