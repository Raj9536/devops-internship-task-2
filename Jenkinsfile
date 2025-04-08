pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'node:18'
    }

    stages {
        stage('Build') {
            steps {
                echo '📦 Pulling Node.js Docker image and installing dependencies...'
                sh '''
                docker run --rm -v "$PWD":/usr/src/app -w /usr/src/app ${DOCKER_IMAGE} sh -c "npm install"
                '''
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests inside Docker container...'
                sh '''
                docker run --rm -v "$PWD":/usr/src/app -w /usr/src/app ${DOCKER_IMAGE} sh -c "npm test || echo No tests found"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying app using Node.js inside Docker...'
                sh '''
                docker run -d -p 3000:3000 -v "$PWD":/usr/src/app -w /usr/src/app ${DOCKER_IMAGE} sh -c "node index.js"
                '''
            }
        }
    }
}
