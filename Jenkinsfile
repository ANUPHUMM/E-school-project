
          pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Checkout the source code from your repository
                checkout scm
                
                // Example: Building HTML files (replace with your build commands)
                sh 'npm install' // or any build commands you use for your HTML project
            }
        }
        
        stage('Test') {
            steps {
                // Example: Run tests for your HTML project (replace with your test commands)
                sh 'npm test' // or any test commands for your HTML project
            }
        }
        
        stage('Deploy') {
            steps {
                // Example: Deploying HTML files to a server (replace with your deployment commands)
                sh 'npm run deploy' // or any deployment commands for your HTML project
            }
        }
    }
    
    // You can add post actions like notifications, cleanup, etc. here if needed
    // Example:
    post {
        always {
            // Example: Sending a notification or performing cleanup tasks
            echo 'Pipeline has completed'
        }
    }
}
