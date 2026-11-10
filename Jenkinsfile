pipeline {
    agent any

    stages {

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/AK-1807/devops-bootcamp-cicd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-bootcamp-cicd .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                docker stop devops-bootcamp-cicd || true
                docker rm devops-bootcamp-cicd || true

                docker run -d \
                  --name devops-bootcamp-cicd \
                  -p 8080:80 \
                  devops-bootcamp-cicd
                '''
            }
        }
    }
}
