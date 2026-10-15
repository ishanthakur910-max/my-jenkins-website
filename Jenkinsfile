pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building website Docker image...'
                sh 'docker build -t my-jenkins-website .'
            }
        }

        stage('Test') {
            steps {
                echo 'Checking if the Docker image was created...'
                sh 'docker image inspect my-jenkins-website'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website...'
                sh 'docker rm -f my-jenkins-website-container || true'
                sh 'docker run -d --name my-jenkins-website-container -p 80:80 my-jenkins-website'
            }
        }
    }
}
