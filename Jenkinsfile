pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', 
                    credentialsId: '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', 
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
                sh 'pm2 restart all || pm2 start index.js'
            }
        }
    }
}
