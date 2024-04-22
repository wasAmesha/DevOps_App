pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git 'https://github.com/wasAmesha/DevOps_App'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Build Docker image
                script {
                    docker.build('add-docker-app')
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                // Run Docker container
                script {
                    docker.image('add-docker-app').run('-p 3000:3000 --name adder-container -d')
                }
            }
        }
        stage('Test Application') {
            steps {
                // Wait for container to start
                sh 'sleep 10'

                // Test application by accessing endpoint
                sh 'curl http://localhost:3000/add/5/10'
            }
        }
    }

    post {
        always {
            // Cleanup: Stop and remove Docker container
            script {
                docker.container('adder-container').stop()
                docker.container('adder-container').remove()
            }
        }
    }
}
