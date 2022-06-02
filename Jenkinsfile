pipeline {
    agent any
    stages {
        stage('Run app from docker-compose file') {
            steps {
                sh 'docker compose run -d --name custom_alpine custom_alpine'
                sh 'docker compose run -d --name custom_postgres --service-ports custom_postgres'
            }
        }
        stage('Approval to kill'){
            steps {
                input "Can we stop and remove the running containers?"
                sh 'docker compose stop'
                sh 'docker compose rm -f'
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