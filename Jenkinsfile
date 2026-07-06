pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/student-ishikakamble/end-to-end-CI-CD-Pipeline.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t flask-devops .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f flask-container || true'
                sh 'docker run -d --name flask-container -p 5000:5000 flask-devops'
            }
        }

        stage('Test') {
            steps {
                sh 'sleep 5'
                sh 'curl http://localhost:5000'
            }
        }
    }
}
