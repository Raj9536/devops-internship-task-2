pipeline {
    agent {
        docker {
            image 'node:18'
        }
    }
    stages {
        stage('Build') {
            steps {
                echo '📦 Installing dependencies...'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo '🧪 Running tests...'
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                echo '🚀 Deploying app...'
                sh 'node index.js'
            }
        }
    }
}
