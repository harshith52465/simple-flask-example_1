pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-demo"
        CONTAINER_NAME = "flask-demo-container"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/harshith52465/demo-app.git'
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
                sh '''
                docker run -d -p 5000:5000 \
                --name $CONTAINER_NAME \
                $IMAGE_NAME
                '''
            }
        }
    }
}

