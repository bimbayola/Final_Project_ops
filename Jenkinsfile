pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'todo-list-node-redis'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/bimbayola/Final_Project.git', branch: 'main'
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
    post {
        success {
            emailext (
                to: 'oj.ola.jastrzebska@gmail.com',
                subject: "Pipeline Success",
                body: "Your Jenkins pipeline executed successfully."
            )
        }
        failure {
            emailext (
                to: 'oj.ola.jastrzebska@gmail.com',
                subject: "Pipeline Failure",
                body: "Your Jenkins pipeline execution failed. Please check the Jenkins console output for details."
            )
        }
    }
}

