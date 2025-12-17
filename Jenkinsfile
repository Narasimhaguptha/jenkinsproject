pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Narasimhaguptha/jenkinsproject.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-webapp:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop webapp || true
                docker rm webapp || true
                docker run -d \
                  --name webapp \
                  -p 80:80 \
                  my-webapp:latest
                '''
            }
        }
    }
}
