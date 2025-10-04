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
                    // Build the Docker image
                    sh '/usr/local/bin/docker build -t devops-first-app .'
                    sh '/usr/local/bin/docker run -d -p 5001:5000 --name devops-first-app devops-first-app'

                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Stop previous container if running
                    sh 'docker ps -q --filter "name=devops-first-app" | xargs -r docker stop'
                    sh 'docker ps -aq --filter "name=devops-first-app" | xargs -r docker rm'

                    // Run the container
                    sh 'docker run -d -p 5001:5000 --name devops-first-app devops-first-app'
                }
            }
        }
    }
}
