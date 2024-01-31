pipeline {
    agent any

    stages {
        stage('Build Nginx') {
            steps {
                script {
                    dir('nginx') {
                        sh 'docker build -t Nginx-image .'
                    }
                }
            }
        }

        stage('Build Apache') {
            steps {
                script {
                    dir('apache') {
                        sh 'docker build -t Apache-image .'
                    }
                }
            }
        }

        stage('Deploy Containers') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
