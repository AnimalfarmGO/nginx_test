pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh ' docker run -it -d -p 9889:80 --name web -v $WORKSPACE/site-content:/usr/share/nginx/html nginx'
            }
        }
        stage('Test HTTP Return Code') {
            steps {
                script {
                    def response = httpRequest 'http://localhost:9889'
                    println("Status: "+response.status)
                    //println("Content: "+response.content)
                    }
            }
        }
        stage('Test Web Page') {
            steps {
                sh '''
                    curl http://localhost:9889 > index.txt
                    md5sum index.txt site-content/index.html > hashes.txt
                    md5sum --check hashes.txt
                    ls 
                    ls site-content
                    curl -o /dev/null -s -w "%{http_code}" http://localhost:9889
                ''' 
            }
        } 
                
        stage('Delete Container') {
            steps {
                sh 'docker rm -f web'
            }
        }
    }
}
