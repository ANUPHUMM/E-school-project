pipeline {
    agent any
    tools {
        maven 'maventest'
        jdk 'jdktest'
    }
    environment {
        SONAR_PROJECT_KEY = 'test'
    } 
    stages {
        stage('Clone sources') {
            steps {
                git url: 'https://github.com/ANUPHUMM/E-school-project.git'
            }
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv(credentialsId: 'test', installationName: 'sonarqubetest') { 
                       sh "./mvnw clean verify -DskipTests=true sonar:sonar -Dsonar.projectKey=$SONAR_PROJECT_KEY"
                }
            }
        }
    }
}
