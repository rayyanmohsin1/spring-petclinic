 
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Run the build
                    sh './mvnw clean package'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests and generate code coverage report with JaCoCo
                    sh './mvnw test'
                }
            }
        }
        stage('Code Coverage') {
            steps {
                script {
                    // Generate code coverage report
                    sh './mvnw jacoco:report'
                }
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'target/site/jacoco/*.html', fingerprint: true
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
