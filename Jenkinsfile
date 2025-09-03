pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: '90338758-95e6-4a53-b964-c7548aba6c01', 
                    url: 'https://github.com/Ashutosh0108/calculator-app.git', 
                    branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'python -m pip install --upgrade pip'
                bat 'if exist requirements.txt pip install -r requirements.txt'
            }
        }

        stage('Run Unit Tests') {
            steps {
                // Discover and run all Python tests in the 'tests' folder
                bat 'python -m unittest discover -s tests -p "*.py" -v'
            }
        }
    }

    post {
        success {
            echo '✅ Build and all tests completed successfully!'
        }
        failure {
            echo '❌ Build or tests failed. Check the console output for details.'
        }
    }
}
