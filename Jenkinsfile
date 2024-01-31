pipeline {
    agent any

    stages {

        stage('Build Nginx') {
            steps {
                script {
                    dir('nginx') {
                        // Build Nginx Docker image
                        sh '/usr/bin/docker build -t Nginx-image .'
                    }
                }
            }
        }

        stage('Build Apache') {
            steps {
                script {
                    dir('apache') {
                        // Build Apache Docker image
                        sh '/usr/bin/docker build -t Apache-image .'
                    }
                }
            }
        }

        stage('Deploy Containers') {
            steps {
                script {
                    // Deploy containers using Docker Compose
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
