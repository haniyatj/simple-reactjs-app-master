pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git branch 'main', url:'https://github.com/haniyatj/simple-reactjs-app-master'
            }
        }
        
        stage('Dependency Installation') {
            steps {
                // Install Node.js dependencies using npm
                bat 'npm install'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                // Build Docker image using Dockerfile
                bat 'docker build -t emily .'
            }
        }
        
        stage('Run Docker Image') {
            steps {
                // Run Docker container from the built image
                bat 'docker run -d -p 8080:8080 emily'
            }
        }
        
        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: '3dad1a07-5720-4c90-8611-b549a64ae36b', url: 'https://docker.io']) {
                    // Push Docker image to Docker Hub
                    bat 'docker push emily'
                }
            }
        }
    }
}
