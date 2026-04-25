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
        
        stage('Test Failure') {
            steps {
                error "This is a forced failure to test my email!"
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            emailext (
                subject: "Build ${currentBuild.result}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """Build ${currentBuild.result}
                        Job: ${env.JOB_NAME}
                        Number: ${env.BUILD_NUMBER}
                        Check console output at: ${env.BUILD_URL}""",
                to: 'retrodante3@gmail.com'
            )
        }
    }
}
