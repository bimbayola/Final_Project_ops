pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'todo-list-node-redis'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'TWOJ_ADRES_DO_REPO', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(env.DOCKER_IMAGE)
                }
            }
        }
        stage('Run Docker Container') {
           steps {
                bat 'docker-compose up -d --build'
            }
        }
    }
}
