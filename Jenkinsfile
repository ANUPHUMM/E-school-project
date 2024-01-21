pipeline {
    agent any

    environment {
        SONARQUBE_URL = 'http://10.13.194.105:9000'
        SONARQUBE_TOKEN = 'test'
        GIT_REPO_URL = 'https://github.com/ANUPHUMM/E-school-project.git'
        SONAR_SCANNER_PATH = '/root/sonarscanner/sonar-scanner-4.6.0.2311-linux/bin/sonar-scanner' // Replace with the actual path
    }

    stages {
        stage('Debug') {
            steps {
                sh 'echo "PATH: ${PATH}"'
                sh 'which sonar-scanner'
                sh 'ls -l /root/sonarscanner/sonar-scanner-4.6.0.2311-linux/bin/sonar-scanner' // Replace with the actual path
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    dir("${WORKSPACE}") {
                        sh "${SONAR_SCANNER_PATH} \
                            -Dsonar.host.url=${SONARQUBE_URL} \
                            -Dsonar.projectKey=E-school-project \
                            -Dsonar.sources=css \
                            -Dsonar.login=${SONARQUBE_TOKEN} \
                            -Dsonar.links.homepage=${GIT_REPO_URL}"
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up workspace and other post-build tasks
            cleanWs()
        }
    }
}
