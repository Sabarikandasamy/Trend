pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "sabari5008/trend-static-app-new:v1"
        AWS_REGION = "ap-south-1"
        CLUSTER_NAME = "trend-cluster-v2"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Sabarikandasamy/Trend.git'
            }
        }

        stage('Build & Push Docker Image') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                        docker login -u $DOCKER_USER -p $DOCKER_PASS
                        docker buildx build \
                          --platform linux/amd64,linux/arm64 \
                          -t $DOCKER_IMAGE \
                          --push .
                    '''
                }
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh '''
                    aws eks update-kubeconfig \
                      --region $AWS_REGION \
                      --name $CLUSTER_NAME

                    kubectl apply -f k8s/
                '''
            }
        }
    }
}

