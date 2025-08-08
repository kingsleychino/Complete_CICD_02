pipeline {
    agent any
    
    stages {
        stage('GitHub') {
            steps {
                git branch: 'main', credentialsId: 'github-cred', url: 'https://github.com/kingsleychino/Complete_CICD_02.git'
            }
        }
    }
}