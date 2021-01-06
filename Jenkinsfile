pipeline {
    agent {
        docker {
            image 'node:8.0.0-alpine'
            args '-p 3000:3000'
            args '-u root:root'
        }
    }
    environment {
        CI = 'true' 
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') { 
            steps {
                sh 'ls'
                sh '/bin/bash -c npm run test'
            }
        }
    }
}
