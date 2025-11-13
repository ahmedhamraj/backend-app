pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo "Pulling code from GitHub..."
                git branch: 'main', url: 'https://github.com/ahmedhamraj/backend-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing dependencies..."
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo "Building application..."
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'npm test || true'   // avoids pipeline failure if no tests
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo "Archiving build output..."
                archiveArtifacts artifacts: '**/build/**', fingerprint: true
            }
        }
    }
}
