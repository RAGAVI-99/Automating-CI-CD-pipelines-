pipeline {
    agent any

    environment {
        IMAGE_NAME = "ci-cd-demo-app"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/your-username/ci-cd-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f demo-app || true'
                sh 'docker run -d -p 3000:3000 --name demo-app $IMAGE_NAME'
            }
        }
    }

    post {
        always {
            echo '✅ CI/CD pipeline finished.'
        }
    }
}
