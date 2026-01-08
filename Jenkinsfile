pipeline {
    agent any
    environment {
        DOCKER_HUB = credentials('docker-hubid')
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t hiya855/hello-rhel-app:latest .'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run --rm hiya855/hello-rhel-app:latest'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh 'echo $DOCKER_HUB_PSW | docker login -u $DOCKER_HUB_USR --password-stdin'
                sh 'docker push hiya855/hello-rhel-app:latest'
            }
        }
    }
}

