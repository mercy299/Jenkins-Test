pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out repository..."
            }
        }

        stage('Build') {
            steps {
                echo "Running build step..."
                sh "python3 app.py"
            }
        }

        stage('Test') {
            steps {
                echo "Running test step..."
                sh "echo 'All tests passed!'"
            }
        }
    }

    post {
        always {
            echo "Pipeline completed."
        }
    }
}
