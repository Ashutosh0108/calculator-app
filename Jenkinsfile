pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Setup Virtual Environment') {
            steps {
                bat "if exist venv rmdir /s /q venv"
                bat "python -m venv venv"
                bat "venv\\Scripts\\python.exe -m pip install --upgrade pip"
                bat "venv\\Scripts\\python.exe -m pip install -r requirements.txt"
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat "venv\\Scripts\\python.exe -m unittest discover -s . -p \"test_*.py\""
            }
        }
    }

    post {
        success {
            echo "✅ Build and all tests passed!"
        }
        failure {
            echo "❌ Build failed or some tests failed. Check console output."
        }
    }
}
