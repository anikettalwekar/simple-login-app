pipeline {
    agent any

    environment {
        APP_DIR = "/var/www/login-app"
        RELEASES_DIR = "/var/www/login-app/releases"
        RELEASE_NAME = "release-${BUILD_NUMBER}"
    }

    stages {
        stage('Deploy (Rolling Style)') {
            steps {
                sh """
                ssh ubuntu@10.0.0.121 '
                  mkdir -p ${RELEASES_DIR}/${RELEASE_NAME}
                '
                
                rsync -avz --delete \
                  --exclude='.git' \
                  --exclude='Jenkinsfile' \
                  ./ ubuntu@10.0.0.121:${RELEASES_DIR}/${RELEASE_NAME}/
                
                ssh ubuntu@10.0.0.121 '
                  ln -sfn ${RELEASES_DIR}/${RELEASE_NAME} ${APP_DIR}/current
                '
                """
            }
        }
    }
}
