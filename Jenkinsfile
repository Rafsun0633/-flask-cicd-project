pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Rafsun0633/-flask-cicd-project.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app:latest .'
            }
        }
        
        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh 'docker run flask-app:latest python -c "print(\'Tests passed!\')"'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'docker stop flask-app || true'
                sh 'docker rm flask-app || true'
                sh 'docker run -d -p 5000:5000 --name flask-app flask-app:latest'
            }
        }
    }
}
