pipeline {
    agent any
    environment {
        DOCKER_HUB = credentials('docker-hub-id')
    }
    stages {
        stage('Login') {
            steps {
               
                sh 'echo $DOCKER_HUB_PSW | docker login -u $DOCKER_HUB_USR --password-stdin'
            }
        }
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
        stage('Push') {
            steps {
                sh 'docker push hiya855/hello-rhel-app:latest'
            }
        }
    }
}
