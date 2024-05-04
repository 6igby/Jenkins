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
        stage('Completed Build Email') {
            steps {
                script {
                    def stageStatus = currentBuild.result ?: 'SUCCESS'
                    if (currentBuild.currentResult == 'FAILURE') {
                        stageStatus = 'FAILURE'
                    }
                    mail bcc: '', body: "Hello,\n\nThis is an email from Jenkins pipeline. The last stage '${stageName}' had a status of ${stageStatus}.\n\nRegards,\nJenkins", cc: '', from: '', replyTo: '', subject: 'EmailJenkinsPipeline', to: 'arr8ws@gmail.com'
                }
            }
        }
    }
}
