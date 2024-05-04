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
                    emailext to: env.EMAIL_RECIPIENTS,
                    subject: "Build Stage Complete",
                    body: "Build stage: ${currentBuild.result}\n\nLogs attached.",
                    attachLog: true
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Run unit tests and integration tests using JUnit and TestNG"
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENTS,
                    subject: "Unit and Integration Tests Stage Complete",
                    body: "Unit and Integration Tests stage: ${currentBuild.result}\n\nLogs attached.",
                    attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Perform code analysis using SonarQube"
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENTS,
                    subject: "Code Analysis Stage Complete",
                    body: "Code Analysis stage: ${currentBuild.result}\n\nLogs attached.",
                    attachLog: true
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo "Perform security scan using OWASP ZAP"
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENTS,
                    subject: "Security Scan Stage Complete",
                    body: "Security Scan stage: ${currentBuild.result}\n\nLogs attached.",
                    attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploy application to AWS EC2 instance using AWS CLI"
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENTS,
                    subject: "Deploy to Staging Stage Complete",
                    body: "Deploy to Staging stage: ${currentBuild.result}\n\nLogs attached.",
                    attachLog: true
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on staging environment using Selenium"
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENTS,
                    subject: "Integration Tests on Staging Stage Complete",
                    body: "Integration Tests on Staging stage: ${currentBuild.result}\n\nLogs attached.",
                    attachLog: true
               }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy application to AWS EC2 instance using AWS CLI"
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENTS,
                    subject: "Deploy to Production Stage Complete",
                    body: "Deploy to Production stage: ${currentBuild.result}\n\nLogs attached.",
                    attachLog: true
                }
            }
        }
    }
}
