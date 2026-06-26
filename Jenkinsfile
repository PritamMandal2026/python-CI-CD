pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/user/hello-app.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t hello-python-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop hello-python-app || true
                docker rm hello-python-app || true

                docker run -d \
                  --name hello-python-app \
                  -p 5000:5000 \
                  hello-python-app
                '''
            }
        }

    }
}