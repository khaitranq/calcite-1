pipeline {
    agent {
        node {
            label 'git-websites'
        }
    }

    environment {
        COMPOSE_PROJECT_NAME = "${env.JOB_NAME}-${env.BUILD_ID}"
    }

    options {
        timeout(time: 20, unit: 'MINUTES')
    }

    stages {
        stage('Build') {
            steps {
                dir ("site") {
                    sh 'docker-compose --verbose run -T -e JEKYLL_UID=$(id -u) -e JEKYLL_GID=$(id -g) build-site'
                }
                echo "Done generating"
            }
        }

        stage('Test') {
            steps {
                echo 'Testing....'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}