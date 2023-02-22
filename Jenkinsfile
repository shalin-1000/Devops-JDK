pipeline {
    agent any

    environment {
        DOCKERHUB_USERNAME = "shalin1000"
        APP_NAME = "python-app"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}" + "/" + "${APP_NAME}"
        REGISTRY_CREDS = 'docker-registrty'
    }

    stages {
        stage ('Cleanup Workspace') {
            steps {
                script {
                    cleanWs()
                }

            }
        }
        stage ('GIT Checkout') {
            steps {
                script {
                    git credentialsId: 'GIT-PAT',
                    url: 'https://github.com/shalin-1000/Devops-JDK',
                    branch: 'main'
                }
            }

        }
        stage ('Build the Image') {
            steps {
                script {
                    docker_image = docker.build "${IMAGE_NAME}"
                }
            }
        }
    }
}
