pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Perform code compilation and packaging with Maven"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Run unit tests and integration tests using JUnit and TestNG"
            }
            post {
                success {
                    email notifyBody: 'Test stage succeeded', recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                    attachLog('test-logs.log')
                }
                failure {
                    email notifyBody: 'Test stage failed', recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                    attachLog('test-logs.log')
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Perform code analysis using SonarQube"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Perform security scan using OWASP ZAP"
            }
            post {
                success {
                    email notifyBody: 'Security scan stage succeeded', recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                    attachLog('security-scan-logs.log')
                }
                failure {
                    email notifyBody: 'Security scan stage failed', recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                    attachLog('security-scan-logs.log')
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploy application to AWS EC2 instance using AWS CLI"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on staging environment using Selenium"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy application to production AWS EC2 instance using AWS CLI"
            }
        }
    }
    post {
        always {
            email notifyBody: 'Pipeline completed', recipientProviders: [[$class: 'DevelopersRecipientProvider']]
        }
    }
}

def attachLog(logFile) {
    emailext attachLog: true, logFile: logFile
}
