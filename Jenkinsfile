pipeline {
    agent any

    stages {
        stage('Source') {
            steps {
                git 'https://github.com/latinvero67/unir-cicd.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building stage!'
                sh 'make build'
            }
        }

        stage('Unit Tests') {
            steps {
                echo 'Running unit tests!'
                sh 'make test-unit'
                archiveArtifacts artifacts: 'results/unit_result.xml'
            }
        }

        stage('API Tests') {
            steps {
                echo 'Running API tests!'
                sh 'make test-api'
                archiveArtifacts artifacts: 'results/api_result.xml'
            }
        }

        stage('End-to-End Tests') {
            steps {
                echo 'Running end-to-end tests!'
                sh 'make test-e2e'
                archiveArtifacts artifacts: 'results/e2e_result.xml'
            }
        }
    }

    post {
        always {
            junit 'results/*.xml'
            cleanWs()
        }
    }
}
