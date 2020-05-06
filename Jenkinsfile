pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Deliver') {
            steps {
                sh 'set -x & npm run start & sleep 1 & echo $! > .pidfile & set +x'
                sh 'set -x & kill $(cat .pidfile)'
            }
        }
    }
}
