pipeline {
    agent any

    stages {
        stage('Deploy to Web Server') {
            steps {
                sh '''
                  rsync -avz --delete \
                  --exclude='.git' \
                  --exclude='Jenkinsfile' \
                  ./ ubuntu@10.0.0.121:/var/www/login-app/
                '''
            }
        }
    }
}
