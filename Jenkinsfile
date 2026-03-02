pipeline {
    agent any

    environment {
        APP_SERVER = "43.205.130.68"   // replace with your App Server IP
    }

    stages {

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Deploy to App Server') {
            steps {
                sh """
                scp -o StrictHostKeyChecking=no -r * ubuntu@${APP_SERVER}:/var/www/pythonapp/

                ssh -o StrictHostKeyChecking=no ubuntu@${APP_SERVER} '
                    pkill -f app.py || true
                    cd /var/www/pythonapp
                    nohup python3 app.py > output.log 2>&1 &
                '
                """
            }
        }
    }
}