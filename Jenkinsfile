stage('SonarQube Analysis') {
    steps {
        withSonarQubeEnv('SonarQube-Server') {
            withCredentials([string(credentialsId: 'sonarqube-token', variable: 'SONAR_TOKEN')]) {
                sh '''
                    /opt/sonar-scanner/bin/sonar-scanner \
                        -Dsonar.projectKey=SonarQube-Task \
                        -Dsonar.projectName="SonarQube Task" \
                        -Dsonar.sources=. \
                        -Dsonar.sourceEncoding=UTF-8 \
                        -Dsonar.token="$SONAR_TOKEN"
                '''
            }
        }
    }
}