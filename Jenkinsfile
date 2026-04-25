pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/KrishnaV432/project-1-devops.git'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t spring-project:v1 .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop petclinic || true'
                sh 'docker rm petclinic || true'
                sh 'docker run -d -p 8085:8085 --name petclinic spring-project:v1'
            }
        }
    }
}
