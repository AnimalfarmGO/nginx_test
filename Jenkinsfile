pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh ' docker run -it -d -p 9889:80 --name web -v $WORKSPACE/site-content:/usr/share/nginx/html nginx'
            }
        }
        stage('Test Web Page') {
            steps {
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                    pwd
                    curl http://localhost:9889
                    curl -o /dev/null -s -w "%{http_code}" http://localhost:9889
                    docker stop web
                    docker rm web
                '''
            }
        }
        stage('Slack') {
            steps {
                slackSend message: 'test message'
            }
        }
    }
}
