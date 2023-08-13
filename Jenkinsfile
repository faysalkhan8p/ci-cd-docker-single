pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t faysalkhan8p/ci-cd-docker-single -f Dockerfile.dev .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    sh 'docker run faysalkhan8p/ci-cd-docker-single npm run test -- --coverage'
                }
            }
        }
    }
}
