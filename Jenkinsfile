pipeline {
    agent {
        docker {
            image 'node'
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
                sh 'rm -rf node_modules'
                sh 'yarn install'
            }
        }
        stage('Test') { 
            steps {
                sh 'ls'
                sh 'yarn test'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'yarn start & sleep 1'
                sh 'echo $! > .pidfile'
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                sh 'kill $(cat .pidfile)'
            }
        }
    }
