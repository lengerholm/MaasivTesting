pipeline {
    agent {
        docker {
            image 'jenkins/jenkins:lts-jdk17'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Output Jenkins PATH') {
            steps {
                sh 'echo $PATH'
            }
        }

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
