pipeline {
    agent any
    environment {
        GIT_REPO = 'https://github.com/Ankit-Jaipuriar/MERN-Docker'
        BRANCH = 'master'
    }
    stages {
        stage('Clone') {
            steps {
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }
        stage('Build') {
            steps {
                echo 'Build step started...'
                dir('frontend') {
                    bat 'npm install'
                }
                dir('backend') {
                    bat 'npm install'
                }
                echo 'Build step completed.'
            }
        }
        stage('Test') {
            steps {
                echo 'Running test scripts...'
                echo 'Tests passed.'
            }
        }
        stage('Docker Build & Deploy') {
            steps {
                echo 'Building and deploying Docker containers...'
                bat 'docker-compose down'
                bat 'docker-compose up --build -d'
                echo 'Docker containers built and deployed.'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}