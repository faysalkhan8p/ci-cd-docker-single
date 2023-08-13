pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image using the Dockerfile.dev file
                    sh 'docker build -t react-app-dev -f Dockerfile.dev .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run the container and execute the tests
                    // The `docker run` command for tests may need to be adjusted based on your specific test setup
                    containerID = sh(script: 'docker run -d react-app-dev npm run test', returnStdout: true).trim()
                    // Wait a bit to let tests finish - adjust as needed
                    sh 'sleep 60' 
                }
            }
        }
    }

    post {
        always {
            script {
                // Stop the container after tests
                sh "docker stop ${containerID}"
            }
        }
    }
}
