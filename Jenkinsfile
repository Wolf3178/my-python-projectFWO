pipeline {
    agent any

    stages {
        stage('check code') {
            steps {
                sh 'python3 -m flake8 . --count --show-source --statistics || true'
            }
        }
        stage('test') {
            steps {
                sh 'pytest | tee report.txt'
            }
        }
        stage('push') {
             steps {
            sh 'docker build -t wolf31/my-python-app:$BUILD_NUMBER .'
            sh 'docker login -u $DOCKER_LOGIN -p $DOCKER_PASS'
            sh 'docker push wolf31/my-python-app:$BUILD_NUMBER'
             }
        }
    }
}

