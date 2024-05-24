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
          post {
        success {
            emailext (
                to: 'your_email@example.com',
                subject: "Build Success: ${currentBuild.fullDisplayName}",
                body: "Congratulations! Your build ${currentBuild.fullDisplayName} was successful."
            )
        }
        failure {
            emailext (
                to: 'your_email@example.com',
                subject: "Build Failure: ${currentBuild.fullDisplayName}",
                body: "Oh no! Your build ${currentBuild.fullDisplayName} failed. Please check Jenkins for details."
            )
        }
    }
    }
}
