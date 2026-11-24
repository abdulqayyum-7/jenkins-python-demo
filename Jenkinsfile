pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Install dependencies') {
            steps {
                sh 'python3 -m pip install --user -r requirements.txt'
            }
        }
        stage('Run tests') {
            steps {
                sh 'python3 -m pytest -q'
            }
        }
    }

    post {
        success { echo 'Build successful: tests passed.' }
        failure { echo 'Build failed: inspect the test output.' }
    }
}
