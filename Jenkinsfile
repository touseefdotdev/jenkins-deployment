pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-flask-app'
        CONTAINER_NAME = 'flask-app-container'
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh "sudo docker build -t ${IMAGE_NAME} ."
            }
        }

        stage('Run Docker Container') {
            steps {
                // Stop old container if running
                sh "sudo docker rm -f ${CONTAINER_NAME} || true"

                // Run new container
                sh "sudo docker run -d --name ${CONTAINER_NAME} -p 5000:5000 ${IMAGE_NAME}"
            }
        }
    }
}