pipeline {
    agent {
        docker {
            image 'jenkins/agent:latest-jdk11'
            args '--network bridge --env DOCKER_HOST=tcp://172.17.0.2:2376 --env DOCKER_TLS_VERIFY=1 --env DOCKER_CERT_PATH=/certs/client'
        }
    }

    stages {

        stage('Build Nginx') {
            steps {
                script {
                    dir('nginx') {
                        // Build Nginx Docker image
                        sh 'docker build -t Nginx-image .'
                    }
                }
            }
        }

        stage('Build Apache') {
            steps {
                script {
                    dir('apache') {
                        // Build Apache Docker image
                        sh 'docker build -t Apache-image .'
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
