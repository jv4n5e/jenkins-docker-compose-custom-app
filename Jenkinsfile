pipeline {
    agent any
    stages {
        stage('Run app from docker-compose file') {
            steps {
                sh 'docker compose run -d --name custom_app custom_app'
            }
        }
    }
    post('If fail, stop and remove containers.'){
        failure {
            sh 'docker compose stop'
            sh 'docker compose rm -f'
        }
    }
}