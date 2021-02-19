pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'env'
                sh 'docker-compose up'
            }
        }
    }
}
