pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/samantha58-bit/my-first-ci-cd-app.git',
                    credentialsId: '396a7278-4a2f-403b-8400-998d12976839'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t student-webapp .'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying container..."
                sh '''
                    docker rm -f student-web || true
                    docker run -d -p 8085:80 --name student-web student-webapp
                '''
            }
        }
    }
}

