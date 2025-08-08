pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }

    stages {
        stage('GitHub') {
            steps {
                git branch: 'main', credentialsId: 'github-cred', url: 'https://github.com/kingsleychino/Complete_CICD_02.git'
            }
        }

        stage('Unit Test') {
            steps {
                sh '''
                    npm test
                    npm install
                '''
            }
        }
    }
}