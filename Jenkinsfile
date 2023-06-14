pipeline {
     agent {
          any
     }
     environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-key')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build the docker image') {
            steps {
                script {
                    // Define dockerImage variable 
                    def dockerImage = docker.build("go/docker", "--file Dockerfile .")
                }
            }
        }
        stage('Docker login') {
            steps {
                script {
                    docker.withRegistry('https://hub.docker.com/r/nabelaashraf/instabug-challenge', 'dockerhub-key') {
                        docker.login()
                    }
                }
            }
        }
        stage('Push the image') {
            steps {
                script {
                    // Access dockerImage variable 
                    docker.withRegistry('https://hub.docker.com/r/nabelaashraf/instabug-challenge', 'dockerhub-key') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
