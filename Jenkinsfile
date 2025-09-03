pipeline {
    agent any

    environment {
        PYTHON_PATH = "C:\\Users\\Admin\\AppData\\Local\\Programs\\Python\\Python313\\python.exe"
    }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat "\"${env.PYTHON_PATH}\" -m pip install --upgrade pip"
                bat "\"${env.PYTHON_PATH}\" -m pip install -r requirements.txt"
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat "\"${env.PYTHON_PATH}\" -m unittest discover"
            }
        }
    }

    post {
        success {
            echo "✅ Build and tests succeeded!"
        }
        failure {
            echo "❌ Build or tests failed. Check console output."
        }
    }
}
