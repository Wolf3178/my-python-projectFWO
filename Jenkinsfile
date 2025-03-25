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
    }
}

