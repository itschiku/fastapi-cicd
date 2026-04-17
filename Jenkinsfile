pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fastapi-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f fastapi-container || true'
                sh 'docker run -d -p 8000:8000 --name fastapi-container fastapi-app'
            }
        }
    }
}
