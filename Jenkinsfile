pipeline {
    agent any
    
    stages {
        stage('Install dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }
        
        stage('Run tests') {
            steps {
                sh './venv/bin/pytest --junitxml=report.xml --cov=tests --cov-report=html --cov-report=term || true'
            }
        }
        
        stage('Publish Report') {
            steps {
                junit 'report.xml'
            }
        }
    }
}