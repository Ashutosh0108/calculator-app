pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Ashutosh0108/calculator-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Upgrade pip
                bat 'python -m pip install --upgrade pip'

                // Install dependencies if requirements.txt exists
                bat 'if exist requirements.txt pip install -r requirements.txt'
            }
        }

        stage('Run Unit Tests') {
            steps {
                // Run all tests in the 'tests' folder
                bat 'python -m unittest discover -s tests'
            }
        }
    }
}
