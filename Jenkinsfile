pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "rakshi06/myapp:${BUILD_NUMBER}"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:${BUILD_NUMBER} .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag myapp:${BUILD_NUMBER} $DOCKER_IMAGE'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'ce67dab9-8ee2-415a-af2b-3ad7aeb5ad82', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run --rm $DOCKER_IMAGE'
            }
        }
    }
}