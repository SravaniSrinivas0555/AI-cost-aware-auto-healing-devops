pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t costaware-app:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop costaware || true
                docker rm costaware || true
                docker run -d -p 5000:5000 --name costaware costaware-app:latest
                '''
            }
        }
    }
}

