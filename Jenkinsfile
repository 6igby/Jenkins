pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Perform code compilation and packaging with Maven"
                git branch: 'main', url: 'https://github.com/6igby/Jenkins.git'
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
    }
    post {
        success {
            mail to: 'arr8ws@gmail.com',
                 subject: 'Succsessful Execution of Build...',
                 body: 'This build has been successful!'
            echo 'Success'
        }
        failure {
            mail to: 'arr8ws@gmail.com',
                 subject: 'Failed Execution of Build...',
                 body: 'This build has failed. Please check the logs.'
            echo 'Failed'
        }
    }
}
