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
                // optional if you have a build step
                sh 'npm run build || true'
            }
        }

        stage('Restart App with PM2') {
            steps {
                sh '''
                pm2 delete all || true
                pm2 start app.js --name node-app
                pm2 save
                '''
            }
        }
    }
}
