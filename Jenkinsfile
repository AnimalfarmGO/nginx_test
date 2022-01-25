pipeline {
    agent {
        docker { 
            image 'nginx:latest'
            args '-p 9889:80'
        }
    }
    stages {
        stage('Test') {
            steps {
                sh 'curl localhost:9889'
            }
        }
    }
}

