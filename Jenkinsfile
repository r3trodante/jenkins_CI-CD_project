pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // This pulls your code from the GitHub repo linked to the job
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                // Compiles the code using Maven
                // Use 'sh' for Linux/macOS or 'bat' for Windows Jenkins agents
                bat 'mvn clean compile'
            }
        }

        stage('Run Application') {
            steps {
                // Executes the main method in App.java
                bat 'mvn exec:java'
            }
        }
    }

    post {
        success {
            echo 'Build and Execution successful!'
        }
        failure {
            echo 'Build failed. Please check the console output for errors.'
        }
    }
}
