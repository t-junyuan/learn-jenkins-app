pipeline {
    agent any

    stages {
        stage('Build Stage') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                    echo "Starting build"
                    npm ci
                    npm run build
                '''
            }
        }

        stage('Test Stage') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                    echo "Test stage"
                    grep 'build/index.html'
                    npm test
                '''
            }
        }
    }
}
