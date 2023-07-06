pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/Abhishek-kurmi/docker-fastapi-test.git'
            }
        }

         stage('Build Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build('fastapi-app:fastapi-app', '.')
            
                }
            }
        }
stage('Deploy') {
    steps {
        bat 'plink root@ec2-18-206-123-165.compute-1.amazonaws.com "mkdir -p /tmp/fastapi"'
		bat 'scp docker-compose.yml root@ec2-18-206-123-165.compute-1.amazonaws.com: /tmp/fastapi'
        bat 'plink root@ec2-18-206-123-165.compute-1.amazonaws.com "cd /tmp/fastapi && docker-compose pull"'
        bat 'plink root@ec2-18-206-123-165.compute-1.amazonaws.com "cd /tmp/fastapi && docker-compose up -d"'
    }
}
    }
}
