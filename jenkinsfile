pipeline {
    agent any
    
    
    stages {
        stage('up') {
            steps {
                sh '/usr/bin/docker-compose up -d'
            }
        }
       
    }
    post {
  success {
    echo 'success'
  }
  failure {
    echo 'failure'
  }
}

}
