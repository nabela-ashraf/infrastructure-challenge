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
                sh 'docker build -t nabelaashraf/instabug-challenge:latest .'
                echo 'build image done'
            }
        }
        stage('Docker login and Push the image') {
            steps {
                sh "echo '$DOCKERHUB_CREDENTIALS_PSW' | docker login -u '$DOCKERHUB_CREDENTIALS_USR' --password-stdin"
                echo 'login done'
                sh 'docker push nabelaashraf/instabug-challenge:latest'
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
