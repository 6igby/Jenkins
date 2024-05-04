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
                script {
                    def powershellCommand  """
                    \$SMTPServer = "smtp.gmail.com"
                    \$SMTPFrom = "arr8ws@gmail.com"
                    \$SMTPTo = "arr8ws@gmail.com"
                    \$SMTPSubject = "Succsessful Execusion of Build..."
                    \$SMTPBody = "This build has been succsessful!"
                    \$SMTPUsername = "arr8ws@gmail.com"
                    \$SMTPPassword = "urca ldxr awox kyzo"
                    Send-MailMessage -From \$SMTPFROM -to \$SMTPTo -Subject \$SMTPSubject -Body \$SMTPBody -SmtpServer \$SMTPServer
                    """
                    powershell(powershellCommand)
                }

                echo 'Succsess'
            }
            failure {
                script{
                    def powershellCommand  """
                    \$SMTPServer = "smtp.gmail.com"
                    \$SMTPFrom = "arr8ws@gmail.com"
                    \$SMTPTo = "arr8ws@gmail.com"
                    \$SMTPSubject = "Succsessful Execusion of Build..."
                    \$SMTPBody = "This build has been succsessful!"
                    \$SMTPUsername = "arr8ws@gmail.com"
                    \$SMTPPassword = "urca ldxr awox kyzo"
                    Send-MailMessage -From \$SMTPFROM -to \$SMTPTo -Subject \$SMTPSubject -Body \$SMTPBody -SmtpServer \$SMTPServer
                    """
                    powershell(powershellCommand)
                }

                echo 'Failed'
            }
    }
}
