pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/Abhishek-kurmi/docker-fastapi-test.git'
            }
        }

        stage('Build and Package') {
            steps {
                sh 'docker build -t your-fastapi-app .'
                sh 'docker save -o your-fastapi-app.tar your-fastapi-app'
            }
        }

        stage('Deploy') {
            steps {
                sh 'scp your-fastapi-app.tar user@your-server:/path/to/destination'
                sh 'ssh user@your-server "docker load -i /path/to/destination/your-fastapi-app.tar"'
                sh 'ssh user@your-server "docker-compose -f /path/to/your/docker-compose.yml up -d"'
            }
        }
    }
}
