pipeline{
    agent any
    environment {
        DIRECTORY_PATH = "http://localhost:8083/job/5.1P_task/"
        TESTING_ENVIRONMENT = "5.1P_environment"
        PRODUCTION_ENVIRONMENT = "Digby"
    }
    stages{
        stage('Build'){
            steps{
                echo "Fetch the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo "Compile the code and generate any necessary artifacts"
            }
        }
        stage('Test'){
            steps{
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }
        stage('Code Quality Check'){
            steps{
                echo "Check the quality of the code"
            }
        }
        stage('Deploy'){
            steps{
                echo "Deploy the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
            }
        }
        stage('Approval'){
            steps{
                echo "Waiting for manual approval..."
                sh 'sleep 10'
            }
        }
        stage('Deploy to Production'){
            steps{
                echo "Deploying the code to the production environment by (${env.PRODUCTION_ENVIRONMENT})"
            }
        }
    }
}