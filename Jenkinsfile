pipeline {
     agent any
     environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-key')
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/nabela-ashraf/infrastructure-challenge.git'
                echo 'Git Checkout'
            }
        }
        stage('Build the docker image') {
            steps {
               sh 'docker build -t go/docker:$BUILD_NUMBER .'
                echo 'build image done'
                }
            }
        }
        stage('Docker login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKER_CREDENTIALS_USER --password-stdin'
                echo 'login done'
                }
            }
        }
        stage('Push the image') {
            steps {
                sh 'docker push go/docker:$BUILD_NUMBER'
                echo 'push image done'
                }
            }
        }
    }
}
