pipeline {
    agent any

    environment {
        SONARQUBE_URL = 'http://10.13.194.105:9000' // Replace with your SonarQube server URL
        SONARQUBE_TOKEN = 'sonartest' // Replace with your SonarQube access token
        GIT_REPO_URL = 'https://github.com/ANUPHUMM/E-school-project.git' // Replace with your GitHub repository URL
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    withSonarQubeEnv('sonarqubetest') {
                        // Run SonarQube analysis
                        sh "sonar-scanner \
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
