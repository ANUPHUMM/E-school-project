pipeline {
    agent any

    environment {
        SONARQUBE_SCANNER_HOME = tool 'SonarQubeScanner'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonartest') {
                    sh "${SONARQUBE_SCANNER_HOME}/bin/sonar-scanner \
                        -Dsonar.projectKey=E-school-project \
                        -Dsonar.sources=css"
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
