pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '.\\gradlew.bat clean build -x test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t max2ba/service-discovery:latest D:/JavaProjects/service-discovery'
            }
        }

        stage('Docker Restart') {
            steps {
                bat '''
                cd /d D:\\JavaProjects\\config-server
                docker compose up -d --build service-discovery
                '''
            }
        }
    }
}
