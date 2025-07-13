pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/bchaithu1947/node.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build || true'
            }
        }

        stage('Start App') {
            steps {
                sh '''
                pm2 delete node-app || true
                pm2 start app.js --name node-app
                pm2 save
                '''
            }
        }
    }
}
