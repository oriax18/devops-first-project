pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh '/usr/local/bin/docker build -t devops-first-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh '/usr/local/bin/docker run -d -p 5001:5000 --name devops-first-app devops-first-app'
                }
            }
        }
    }
}
