pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/Ahishekoza/CI-CD-Project-New.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t abhi2903/nodeapp .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push abhi2903/nodeapp'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}

