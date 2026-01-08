pipeline {
    agent any
    environment {
        // This connects to the 'docker-hub-id' you created in the Jenkins UI
        DOCKER_HUB = credentials('docker-hub-id')
    }
    stages {
        stage('Build') {
            steps {
                // We tag the image with your username so Docker Hub knows where it belongs
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
                // 1. Securely login using the credential variables
                // 2. The password/token is masked as **** in the logs for security
                sh 'echo $DOCKER_HUB_PSW | docker login -u $DOCKER_HUB_USR --password-stdin'
                
                // 3. Push the image to your repository
                sh 'docker push hiya855/hello-rhel-app:latest'
            }
        }
    }
}
