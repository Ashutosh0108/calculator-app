pipeline {
    agent any

    stages {
        // 1️⃣ Checkout the latest code from your Git repo
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        // 2️⃣ Setup virtual environment and install dependencies
        stage('Setup Virtual Environment') {
            steps {
                // Create venv
                bat "python -m venv venv"
                
                // Upgrade pip inside venv
                bat "venv\\Scripts\\python.exe -m pip install --upgrade pip"
                
                // Install required dependencies from requirements.txt
                bat "venv\\Scripts\\python.exe -m pip install -r requirements.txt"
            }
        }

        // 3️⃣ Run Unit Tests
        stage('Run Unit Tests') {
            steps {
                // Discover and run all tests starting with test_*.py
                bat "venv\\Scripts\\python.exe -m unittest discover"
            }
        }
    }

    // 4️⃣ Post actions
    post {
        success {
            echo "✅ Build and tests succeeded!"
        }
        failure {
            echo "❌ Build or tests failed. Check console output."
        }
    }
}
