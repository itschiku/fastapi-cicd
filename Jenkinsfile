pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/<your-username>/fastapi-cicd.git',
                credentialsId: 'github-creds'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("fastapi-app")
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    sh 'docker rm -f fastapi-container || true'
                    sh 'docker run -d -p 8000:8000 --name fastapi-container fastapi-app'
                }
            }
        }
    }
}