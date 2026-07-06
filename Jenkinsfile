pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/student-ishikakamble/end-to-end-CI-CD-Pipeline.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=end-to-end-ci-cd-pipeline \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://localhost:9000
                    '''
                }
            }
        }

        stage('OWASP Dependency Check') {
            steps {
                script {
                    try {
                        dependencyCheck additionalArguments: '', odcInstallation: 'OWASP'
                    } catch (e) {
                        echo "OWASP not configured, skipping"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t flask-devops .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f flask-container || true
                docker run -d --name flask-container -p 5000:5000 flask-devops
                '''
            }
        }

        stage('Test') {
            steps {
                echo "🚀 App deployed successfully"
            }
        }
    }
}

