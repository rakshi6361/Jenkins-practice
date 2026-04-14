pipeline {
    agent any

    environment {
        APP_ENV = "dev"
    }

    stages {

        stage('Build') {
            steps {
                echo "Building application..."
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
            }
        }

        stage('Deploy to Dev') {
            steps {
                sh './hello.sh'
            }
        }

        stage('Approval') {
            steps {
                input "Approve deployment to production?"
            }
        }

        stage('Deploy to Prod') {
            steps {
                echo "Deploying to production..."
            }
        }
    }
}