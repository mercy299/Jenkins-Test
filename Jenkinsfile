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

        stage('Sonar Analysis') {
          steps {
            withSonarQubeEnv('SonarQube') {
              sh "sonar-scanner"
            }
          }
        }
        
        stage('Quality Gate') {
          steps {
            timeout(time: 1, unit: 'HOURS') {
              waitForQualityGate abortPipeline: true
            }
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
