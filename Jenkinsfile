pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Directly check out from 'main' branch
                git branch: 'main', url: 'https://github.com/hafiz-syed-burhan/nextflix.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install everything including TS and types
                sh '''
                    yarn install
                    yarn add --dev typescript @types/react
                '''
            }
        }

        stage('Build') {
            steps {
                // Clean and build
                sh '''
                    rm -rf .next
                    yarn build
                '''
            }
        }

        stage('Run App') {
            steps {
                // Optional: only needed if you want to run the app on Jenkins
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
