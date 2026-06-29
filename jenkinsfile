pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-docker-project .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f jenkins-docker-project || true'
                sh 'docker run -d --name jenkins-docker-project -p 80:80 jenkins-docker-project'
            }
        }
    }
}
