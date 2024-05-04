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
        }
        stage('Code Analysis') {
            steps {
                echo "Perform code analysis using SonarQube"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Perform security scan using OWASP ZAP"
                mail bcc: '', body: 'The Security Scan has been Succsessfully Completed.', cc: '', from: '', replyTo: '', subject: 'Security Test Complete', to: 'arr8ws@gmail.com'
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
        stage('Download') {
            steps {
                sh 'echo "artifact file" > generatedFile.txt'
            }
        }
    }
        post {
            success {
                sendEmailNotification('Success', currentBuild)
            }
            failure {
                sendEmailNotification('Failure', currentBuild)
        }
    }
}

def sendEmailNotification(status, currentBuild) {
    def logs = currentBuild.rawBuild.getLog(1000)

    def emailSubject = "Security Scan ${status}"
    def emailBody = "The Security Scan has ${status}.\n"
    def toEmail = "arr8ws@gmail.com"

    emailext (
        subject: emailSubject,
        body: emailBody,
        to: toEmail,
        attachmentsPattern: '*.log',
        mimeType: 'text/plain',
        attachLog: true
    )
}
