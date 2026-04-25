pipeline {
    agent {
        label 'nodegroup1' 
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Package') {
            steps {
                sh 'mvn clean package' 
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Build packaged and archived.'
        }
    }
}
