pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out project from GitHub'
                checkout scm
            }
        }

        stage('Check Project Files') {
            steps {
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube-Server') {
                    sh '''
                        /opt/sonar-scanner/bin/sonar-scanner \
                            -Dsonar.projectKey=SonarQube-Task \
                            -Dsonar.projectName="SonarQube Task" \
                            -Dsonar.sources=. \
                            -Dsonar.sourceEncoding=UTF-8
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'SonarQube analysis completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the Jenkins console output.'
        }
    }
}