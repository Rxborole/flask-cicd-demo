pipeline {
    agent any

    environment {
        VENV = "venv"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Rxborole/flask-cicd-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh '''
                python3 -m venv $VENV
                . $VENV/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                . $VENV/bin/activate
                pytest
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Deploying to Staging..."
                nohup python app.py &
                '''
            }
        }
    }

    post {

        success {
            emailext(
                subject: "SUCCESS: Jenkins Build",
                body: "Build completed successfully.",
                to: "rupeshb8087@gmail.com"
            )
        }

        failure {
            emailext(
                subject: "FAILED: Jenkins Build",
                body: "Build failed. Please check Jenkins.",
                to: "rupeshb8087@gmail.com"
            )
        }
    }
}