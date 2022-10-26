pipeline {
    agent any

    stages {
        stage('checkout') {
           steps {
             git branch: 'main', url: 'git@github.com:sompallemuktheswar/pipeline.git'
           }
        }
        stage('ECR login') {
            steps {
               sh 'aws ecr get-login-password --region eu-west-3 | sudo docker login --username AWS --password-stdin 121835848081.dkr.ecr.eu-west-3.amazonaws.com'
 
            }
        }
        stage('build image ') {
            steps {
               sh 'sudo docker build -t 121835848081.dkr.ecr.eu-west-3.amazonaws.com/sunny:$ BUILD_NUMBER .'
            }
        }
        stage('push image to ECR Repo') {
            steps {
              sh  'sudo docker push 121835848081.dkr.ecr.eu-west-3.amazonaws.com/sunny:$BUILD_NUMBER'
            }
        }
    }
}


