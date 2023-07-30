pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the Git repository
                git 'your_git_repository_url'
            }
        }

        stage('Build') {
            steps {
                // Clean and build the Maven project
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run tests, if applicable
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            environment {
                // Set environment variables for your deployment
                SERVER_USERNAME = 'your_server_username'
                SERVER_IP = 'your_server_ip'
                DEPLOY_PATH = '/path/to/deploy'
            }
            steps {
                // Assuming you have a target server where you want to deploy the application
                // Replace 'your_server_username', 'your_server_ip', and '/path/to/deploy' with actual values
                // For simplicity, we'll use SSH to copy the JAR file to the server
                sh "ssh ${SERVER_USERNAME}@${SERVER_IP} 'mkdir -p ${DEPLOY_PATH}'"
                sh "scp target/hello-world.jar ${SERVER_USERNAME}@${SERVER_IP}:${DEPLOY_PATH}"
            }
        }
    }

    post {
        always {
            // Clean up workspace or perform other tasks, if needed
        }
    }
}
