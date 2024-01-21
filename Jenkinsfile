pipeline {
    agent any

    stages {
        stage('Clone sources') {
            steps {
                git url: 'https://github.com/ANUPHUMM/E-school-project.git'
            }
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqubetest') {
                    echo 'test'
                }
            }
        }
        stage("Quality gate") {
            steps {
                echo 'test'
            }
        }
    }
}
