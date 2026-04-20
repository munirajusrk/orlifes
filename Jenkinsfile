pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-website"
        CONTAINER_NAME = "website-container"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/munirajusrk/orlifes.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 6000:6000 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}
