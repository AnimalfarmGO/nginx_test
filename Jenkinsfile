pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'nginx:latest'
                    // Run the container on the node specified at the top-level of the Pipeline, in the same workspace, rather than on a new node entirely:
                    // args '-d -it --entrypoint=/bin/sh -p 8088:80 --name web -v index.html:/usr/share/nginx/html'
                    args '-p 9889:80' // -v  index.html:/usr/share/nginx/html'
                    reuseNode true
                }
            }
            steps {
                sh 'ls'
                sh 'pwd'
                sh 'hostname'
                // sh "curl  10.128.0.26"
                sh "curl  10.128.0.26:9889"
            }
        }
        //stage("Test") {
        //    steps {
        //        sh "curl  localhost:9889"
        //    }
       // }
    }
}

