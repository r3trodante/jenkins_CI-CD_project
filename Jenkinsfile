pipeline {
    agent any
    
    tools {
        // Replace 'Maven3' with the EXACT name you gave Maven 
        // in Manage Jenkins -> Tools -> Maven installations
        maven 'MAVEN_HOME' 
    }

    stages {
        stage('Compile') {
            steps {
                // 'bat' is correct for your Windows environment
                bat 'mvn clean compile'
            }
        }

        stage('Run Application') {
            steps {
                bat 'mvn exec:java'
            }
        }
    }

    post {
        success {
            echo 'Build and Execution successful!'
        }
        failure {
            echo 'Build failed. Checking "Tools" configuration might help.'
        }
    }
}
