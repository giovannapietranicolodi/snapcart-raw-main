pipeline {
    agent any

    environment {
        IMAGE_NAME = 'snapcart'
        IMAGE_TAG  = "${env.BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                // Jenkins checks out your repository automatically
                // when Pipeline script from SCM is configured.
                // This stage makes the step explicit.
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building ${IMAGE_NAME}:${IMAGE_TAG}"
                sh "docker version"
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
                sh "docker images ${IMAGE_NAME}:${IMAGE_TAG}"
            }
        }

    }

    post {
        success {
            echo "Build succeeded. Image: ${IMAGE_NAME}:${IMAGE_TAG} built successfully."
        }
        failure {
            echo 'Build failed. Check the console output above.'
        }
    }
}
