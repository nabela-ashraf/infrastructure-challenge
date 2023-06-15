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
        stage('Docker login and Push the image') {
            steps {
                sh "echo '$DOCKERHUB_CREDENTIALS_PSW' | docker login -u '$DOCKERHUB_CREDENTIALS_USR' --password-stdin"
                echo 'login done'
                sh 'docker push [docker.io/nabelaashraf/instabug-challenge]'
                echo 'push image done'
            }
        }
    }
    post {
        always {
          sh 'docker logout'
        }
    }
  }
