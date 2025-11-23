pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/<username>/my-first-ci-cd-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t student-webapp .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f student-web || true
                    docker run -d -p 8085:80 --name student-web student-webapp
                '''
            }
        }
    }
}

