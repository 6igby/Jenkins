pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build the code'
                sh 'mvn clean install' 
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Run unit tests and integration tests'
                sh 'mvn test' 
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyze code quality and security'
                sh 'mvn sonar:sonar' 
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Scan for security vulnerabilities'
                sh 'owasp-zap-command' /
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploy to staging environment'
                sh 'ansible-playbook -i inventory.ini staging.yml' 
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Run integration tests on staging environment'
                sh 'cucumber' 
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploy to production environment'
                sh 'ansible-playbook -i inventory.ini production.yml' 
            }
        }
    }

    post {
        success {
            stage('Send Notification Email') {
                steps {
                    emailext to: 's222465543@deakin.edu.au',
                             subject: 'Pipeline Status: ${currentBuild.result}',
                             body: 'Pipeline status: ${currentBuild.result}',
                             attachLog: true
                }
            }
        }
        failure {
            stage('Send Notification Email') {
                steps {
                    emailext to: 's222465543@deakin.edu.au',
                             subject: 'Pipeline Status: ${currentBuild.result}',
                             body: 'Pipeline status: ${currentBuild.result}',
                             attachLog: true
                }
            }
        }
    }
}
