pipeline {
  agent any  
  options {
    // Keep the 10 most recent builds
    buildDiscarder(logRotator(numToKeepStr:'10')) 
  }
  stages {
    stage ('Build') { 
      steps {
        // install required gems
        sh 'bundle install'

           stage ('TEST') { 
      steps {
        // install required gems
        sh 'bundle TEST'
        // publish html
        publishHTML target: [
            allowMissing: false,
            alwaysLinkToLastBuild: false,
            keepAll: true,
            reportDir: 'coverage',
            reportFiles: 'home.htm',
            reportName: 'RCov Report'
          ]
      }
    }
    }
  }
}
