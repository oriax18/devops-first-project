pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/oriax18/devops-first-project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("devops-first-app")
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Stop old container if running
                    sh 'docker ps -q --filter "name=devops-first-app" | xargs -r docker stop'
                    sh 'docker ps -aq --filter "name=devops-first-app" | xargs -r docker rm'

                    docker.image("devops-first-app").run("-p 5001:5000")
                }
            }
        }
    }
}
