pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/hafiz-syed-burhan/nextflix.git'
            }
        }

        stage('Install Dependencies + TypeScript') {
            steps {
                sh '''
                    yarn install
                    yarn add --dev typescript @types/react
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    rm -rf .next
                    yarn build
                '''
            }
        }

        stage('Run App') {
            steps {
                sh 'yarn start &'
            }
        }
    }

    post {
        success {
            echo '✅ Build and run successful!'
        }
        failure {
            echo '❌ Something went wrong.'
        }
    }
}
