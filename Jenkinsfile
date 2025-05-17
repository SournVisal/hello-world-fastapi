pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
        IMAGE_NAME = 'yourusername/fastapi-hello-world'
        IMAGE_TAG = "${env.BUILD_NUMBER}"
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/fastapi-hello-world.git'
            }
        }
        stage('Test') {
            steps {
                sh 'docker-compose run app pytest'
            }
        }
        stage('Build and Push') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG   sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push $IMAGE_NAME:$IMAGE_TAG'
            _