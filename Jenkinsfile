pipeline {
    agent any

    triggers {
        cron('H/1 * * * *') // Runs every 1 minute
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', 
                    credentialsId: 'f9cd9239-63a2-4030-b75a-51307f47997f', 
                    url: 'https://github.com/wajahatalli/cicd-test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    pm2 delete index || true  # Delete existing process if running
                    pm2 start index.js --name "index" # Start a fresh process
                    pm2 save  # Save PM2 process list
                '''
            }
        }
    }
}
