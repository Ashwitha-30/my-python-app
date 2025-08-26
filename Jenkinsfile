pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/my-python-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh '. venv/bin/activate && pytest || true'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Flask app...'
                sh 'nohup . venv/bin/activate && python app.py &'
            }
        }
    }
}
