pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/SravaniSrinivas0555/AI-cost-aware-auto-healing-devops.git'
            }
        }

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

