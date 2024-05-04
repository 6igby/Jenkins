pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                task: 'Build the code'
                tool: 'Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                task: 'Run unit tests and integration tests'
                tool: 'JUnit, TestNG'
            }
        }
        stage('Code Analysis') {
            steps {
                task: 'Analyze code quality and security'
                tool: 'SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                task: 'Scan for security vulnerabilities'
                tool: 'OWASP ZAP'
            }
        }
        stage('Deploy to Staging') {
            steps {
                task: 'Deploy to staging environment'
                tool: 'Ansible'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                task: 'Run integration tests on staging environment'
                tool: 'Cucumber'
            }
        }
        stage('Deploy to Production') {
            steps {
                task: 'Deploy to production environment'
                tool: 'Ansible'
            }
        }
    }

    post {
        success {
            stage('Send Notification Email') {
                steps {
                    mail to: 's222465543@deakin.edu.au',
                         subject: 'Pipeline Status: ${currentBuild.result}',
                         body: 'Pipeline status: ${currentBuild.result}',
                         attachments: 'logs.txt'
                }
            }
        }
        failure {
            stage('Send Notification Email') {
                steps {
                    mail to: 's222465543@deakin.edu.au',
                         subject: 'Pipeline Status: ${currentBuild.result}',
                         body: 'Pipeline status: ${currentBuild.result}',
                         attachments: 'logs.txt'
                }
            }
        }
    }
}
