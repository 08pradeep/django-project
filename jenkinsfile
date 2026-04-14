pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'git@github.com:08pradeep/django-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t django-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop django-container || true
                docker rm django-container || true
                docker run -d -p 8000:8000 --name django-container django-app
                '''
            }
        }
    }
}
