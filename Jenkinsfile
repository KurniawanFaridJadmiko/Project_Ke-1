pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('kurniawanfarid1215-dockerhub')
    }
    stages { 

        stage('Build docker image') {
            steps { 
                def isValidTag = (env.BUILD_NUMBER =~ /^[a-zA-Z0-9_.-]{1,127}$/).matches()
                if (!isValidTag) {
                    error "BUILD_NUMBER contains invalid characters."
                }
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
        stage('Run') {
            steps{
                sh 'docker run -p 3000:3000 -d kurniawanfarid1215/tugas1:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
