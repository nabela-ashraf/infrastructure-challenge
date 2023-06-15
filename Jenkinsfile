pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-key')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Git Checkout'
            }
        }
        stage('Build the docker image') {
            steps {
                sh 'docker build -t go/docker .'
                echo 'build image done'
            }
        }
        stage('Docker login') {
            steps {
                sh "echo '$DOCKERHUB_CREDENTIALS_PSW' | docker login -u '$DOCKERHUB_CREDENTIALS_USR' --password-stdin"
                echo 'login done'
            }
        }
        stage('Push the image') {
            steps {
                script {
                    docker.withRegistry('https://hub.docker.com/r/nabelaashraf/instabug-challenge', 'dockerhub-key') {
                        def customImage = docker.image("${env.DOCKER_IMAGE}:${env.DOCKER_TAG}")
                        customImage.push()
                    }
                }
            }
        }
    }
    post {
        always {
          sh 'docker logout'
        }
    }
}
