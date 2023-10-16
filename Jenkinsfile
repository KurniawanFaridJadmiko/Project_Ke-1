pipeline {
    agent any 
    environment {
        DOCKERHUB_CREDENTIALS = credentials('kurniawanfarid1215-dockerhub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t kurniawanfarid1215/tugas1:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push kurniawanfarid1215/tugas1:$BUILD_NUMBER'
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    dockerContainer = docker.image('kurniawanfarid1215/tugas1:$BUILD_NUMBER').run('-p 8080:80 -d')
                }
            }
        }
    }

    post {
        always {
            script {
                dockerContainer.stop()
                dockerContainer.remove()
            }
        }
    }
}
