pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Python application'
                bat '''
                    python --version
                    python -m py_compile app.py
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                bat '''
                    python -m unittest discover
                '''
            }
        }

        stage('Run Application') {
            steps {
                echo 'Running Python application'
                bat '''
                    python app.py
                '''
            }
        }
    }

    post {
        success {
            echo 'CI pipeline completed successfully!'
        }
        failure {
            echo 'CI pipeline failed'
        }
    }
}
