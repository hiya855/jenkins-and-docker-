pipeline {
    agent any 
    stages {
        stage( 'Build') {
            steps {
                sh 'docker build -t hello-rhel-app .'
            }
         }
        stage ('Test') {
            steps {
                sh ' docker run -- hello-rhel-app'
            }
        }
     }
}
