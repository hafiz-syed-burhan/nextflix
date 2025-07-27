pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ayushiee/nextflix.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'yarn install'
            }
        }

        stage('Build') {
            steps {
                sh 'yarn build'
            }
        }

        stage('Run App') {
            steps {
                echo 'You can run the app manually with: yarn start'
            }
        }
    }

    post {
        success {
            echo '🎉 Nextflix app built successfully!'
        }
        failure {
            echo '❌ Something went wrong.'
        }
    }
}
