def remote = [:]
remote.name = "ec2-18-229-56-198.sa-east-1.compute.amazonaws.com"
remote.host = "ec2-18-229-56-198.sa-east-1.compute.amazonaws.com"
remote.allowAnyHosts = true
remote.user = 'ubuntu'

pipeline {
    agent any

    stages {
        stage('Deploy') {
                steps {
                    script {
                            withCredentials([sshUserPrivateKey(credentialsId: 'aws-ec2', keyFileVariable: 'identity', passphraseVariable: '', usernameVariable: 'ubuntu')]) {
                                remote.identityFile = identity
                                sshCommand remote: remote, command: 'cd /home/django-webapp/star_wars;docker-compose stop; sudo git pull origin master; docker-compose up -d'
                            }

                    }
                }
            }
    }
}
