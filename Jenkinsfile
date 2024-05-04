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
            }
            post {
                always {
                    mail to: 'arr8ws@gmail.com', subject: 'Build status', attachLog: ['path/to/logfile1.log', 'path/to/logfile2.log']
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
                echo "Deploy application to AWS EC2 instance using AWS CLI"
            }
            post {
                always {
                    mail to: 'arr8ws@gmail.com', subject: 'Build status', attachLog: ['path/to/logfile1.log', 'path/to/logfile2.log']
                }
            }
        }
    }
}
