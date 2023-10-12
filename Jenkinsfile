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
                sh 'docker build -t kurniawanfarid1215/baruu:2 .'
            }
        }
        // ...Tambahkan tahapan lain seperti pengujian, implementasi, dll.
    }
}
