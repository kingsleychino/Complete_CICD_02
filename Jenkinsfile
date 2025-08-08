pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }

    environment {
        SONAR_PROJECT_KEY = 'Complete-cicd-02'
        SONAR_SCANNER_HOME = tool 'SonarQubeScanner'
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
        stage('SOnarQube Analysis') {
            steps {
                withCredentials([string(credentialsId: 'complete-cicd-02-sonarqube', variable: 'SONAR_TOKEN')]) {
                    withSonarQubeEnv('SonarQube') {
                        sh '''
                            ${SONAR_SCANNER_HOME}/bin/sonar-scanner \
                            -Dsonar.projectKey=$(SONAR_PROJECT_KEY) \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=http://sonarqube-jenkins:9000 \
                            -Dsonar.login=${SONAR_TOKEN}
                        '''
                    }
                }
            }
        }
    }
}