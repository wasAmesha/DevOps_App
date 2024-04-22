pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository
                git 'https://github.com/wasAmesha/DevOps_App'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Build Docker image
                script {
                    docker.build('adder-node-app')
                }
            }
        }
        stage('Run Container') {
            steps {
                // Run Docker container
                script {
                    docker.image('adder-node-app').run("-d -p 3000:3000")
                }
            }
        }
    }
}
