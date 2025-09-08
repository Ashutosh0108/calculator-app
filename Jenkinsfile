pipeline {
    agent any

    stages {
        // 1️⃣ Checkout the latest code from Git
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        // 2️⃣ Setup virtual environment and install dependencies
        stage('Setup Virtual Environment') {
            steps {
                // Delete old venv if it exists
                bat "if exist venv rmdir /s /q venv"

                // Create a new virtual environment
                bat "python -m venv venv"

                // Upgrade pip inside venv
                bat "venv\\Scripts\\python.exe -m pip install --upgrade pip"

                // Install dependencies
                bat "venv\\Scripts\\python.exe -m pip install -r requirements.txt"
            }
        }

        // 3️⃣ Run Unit Tests
        stage('Run Unit Tests') {
            steps {
                // Discover and run all tests starting with test_*.py
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
