pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/anikettalwekar/simple-login-app.git'
            }
        }

        stage('Deploy to Web Server') {
            steps {
                sh '''
                  rsync -avz --delete \
                  ./ ubuntu@10.0.0.121:/var/www/login-app/
                '''
            }
        }
    }
}
