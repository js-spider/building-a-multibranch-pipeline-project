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
                sh 'npm run start & sleep 1'
                sh 'echo $! > .pidfile'
                sh 'kill $(cat .pidfile)'
            }
        }
    }
}
