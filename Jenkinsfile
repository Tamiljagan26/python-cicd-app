pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo "Code already pulled from GitHub"
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo "No tests added yet"
            }
        }
    }
}