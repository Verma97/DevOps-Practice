pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the Git repository
                git 'https://github.com/Verma97/DevOps-Practice.git'
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
                SERVER_USERNAME = 'ec2-user'
                SERVER_IP = '3.80.149.180'
                DEPLOY_PATH = '/home/ec2-user/Project'
            }
            steps {
                // Assuming you have a target server where you want to deploy the application
                // Replace 'your_server_username', 'your_server_ip', and '/path/to/deploy' with actual values
                // For simplicity, we'll use SSH to copy the JAR file to the server
                sh "ssh ${env.ec2-user}@${env.3.80.149.180} 'mkdir -p ${env./home/ec2-user/Project}'"
                sh "scp target/hello-world.jar ${env.ec2-user}@${env.3.80.149.180}:${env./home/ec2-user/Project}"
            }
        }
    }

    post {
        always {
            // Clean up workspace or perform other tasks, if needed
        }
    }
}
