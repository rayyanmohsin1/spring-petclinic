pipeline {
    agent any
    triggers {
        cron('H/10 * * * 1')  
    }
    stages {
        stage('Build') {
            steps {
             
                bat './mvnw.cmd clean package'
            }
        }
        stage('Test and Code Coverage') {
            steps {
               
                bat './mvnw.cmd test jacoco:report'
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
