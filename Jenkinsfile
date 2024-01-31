pipeline {
    agent any
    stages {
        stage('Debug') {
          steps {
              script {
                  sh 'cat /etc/hosts'
              }
          }
        }

        stage('Build Nginx') {
            steps {
                script {
                    dir('nginx') {
                        // Build Nginx Docker image
                        sh 'docker build -t Nginx-image --build-arg DOCKER_HOST=127.0.0.1 .'
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
