pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-taskflow',
                    url: 'https://github.com/adhiraj15/taskflow.git'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t taskflow:jenkins .'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker rm -f taskflow || true'
                sh 'docker run -d --name taskflow -p 5000:5000 taskflow:jenkins'
            }
        }

        stage('Health Check') {
            steps {
                retry(5) {
                    sleep 10
                    sh 'curl -f http://localhost:5000'
                }
            }
        }
    }
}
