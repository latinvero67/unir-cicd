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


    }

}

