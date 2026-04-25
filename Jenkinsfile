pipeline {
    agent any
    
    tools {
        maven 'Maven3' // Ensure this matches your Tool name
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Package') {
            steps {
                // Creates the executable .jar file in the target folder
                bat 'mvn clean package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Saves the .jar file so it appears on the Jenkins project page
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Build packaged and archived.'
            // Optional: Slack/Email notification would go here
        }
        failure {
            echo 'FAILURE: Check Maven logs.'
        }
    }
}
