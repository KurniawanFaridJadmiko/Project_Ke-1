pipeline {
    agent {
        docker {
            image 'maven:3.8.4'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        // ...Tambahkan tahapan lain seperti pengujian, implementasi, dll.
    }
}
