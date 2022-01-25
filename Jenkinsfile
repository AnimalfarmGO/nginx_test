pipeline {
  agent {  }
  stages {
    stage ('Building') {
      steps {
        sh '''
        docker run -it -d -p 9889:80 --name web -v index.html:/usr/share/nginx/html nginx
        curl localhost:9889
        '''  
      }
    }
  }
}
