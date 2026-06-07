pipeline {

    agent any

    stages {

        stage('Clone Repo') {

            steps {

                git 'https://github.com/RashwinPonnanna/amazon-clone.git'
            }
        }

        stage('Build Docker Image') {

            steps {

                sh 'docker build -t amazon-clone:v1 .'
            }
        }

        stage('Deploy Container') {

            steps {

                sh '''
                docker stop amazon-container || true
                docker rm amazon-container || true

                docker run -dit \
                -p 3000:3000 \
                --name amazon-container \
                amazon-clone:v1
                '''
            }
        }
    }
}
