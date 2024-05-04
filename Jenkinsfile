pipeline {
    agent any

    environment {
        EMAIL_RECIPIENTS = 'arr8ws@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo "Perform code compilation and packaging with Maven"
            }
            post {
                always {
                    echo "Sending email notification for Build stage"
                    mail bcc: '', body: "Build stage: ${currentBuild.result}\n\nLogs attached.", cc: '', from: '', replyTo: '', subject: 'Build Stage Complete', to: env.EMAIL_RECIPIENTS, attachLog: true
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Run unit tests and integration tests using JUnit and TestNG"
            }
            post {
                always {
                    echo "Sending email notification for Unit and Integration Tests stage"
                    mail bcc: '', body: "Unit and Integration Tests stage: ${currentBuild.result}\n\nLogs attached.", cc: '', from: '', replyTo: '', subject: 'Unit and Integration Tests Stage Complete', to: env.EMAIL_RECIPIENTS, attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Perform code analysis using SonarQube"
            }
            post {
                always {
                    echo "Sending email notification for Code Analysis stage"
                    mail bcc: '', body: "Code Analysis stage: ${currentBuild.result}\n\nLogs attached.", cc: '', from: '', replyTo: '', subject: 'Code Analysis Stage Complete', to: env.EMAIL_RECIPIENTS, attachLog: true
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo "Perform security scan using OWASP ZAP"
            }
            post {
                always {
                    echo "Sending email notification for Security Scan stage"
                    mail bcc: '', body: "Security Scan stage: ${currentBuild.result}\n\nLogs attached.", cc: '', from: '', replyTo: '', subject: 'Security Scan Stage Complete', to: env.EMAIL_RECIPIENTS, attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploy application to AWS EC2 instance using AWS CLI"
            }
            post {
                always {
                    echo "Sending email notification for Deploy to Staging stage"
                    mail bcc: '', body: "Deploy to Staging stage: ${currentBuild.result}\n\nLogs attached.", cc: '', from: '', replyTo: '', subject: 'Deploy to Staging Stage Complete', to: env.EMAIL_RECIPIENTS, attachLog: true
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on staging environment using Selenium"
            }
            post {
                always {
                    echo "Sending email notification for Integration Tests on Staging stage"
                    mail bcc: '', body: "Integration Tests on Staging stage: ${currentBuild.result}\n\nLogs attached.", cc: '', from: '', replyTo: '', subject: 'Integration Tests on Staging Stage Complete', to: env.EMAIL_RECIPIENTS, attachLog: true
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy application to production AWS EC2 instance using AWS CLI"
            }
            post {
                always {
                    echo "Sending email notification for Deploy to Production stage"
                    mail bcc: '', body: "Deploy to Production stage: ${currentBuild.result}\n\nLogs attached.", cc: '', from: '', replyTo: '', subject: 'Deploy to Production Stage Complete', to: env.EMAIL_RECIPIENTS, attachLog: true
                }
            }
        }
    }
}
