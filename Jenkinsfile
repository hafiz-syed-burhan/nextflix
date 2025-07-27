pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ayushiee/nextflix.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'yarn install'
            }
        }

        stage('Install TypeScript') {
            steps {
                sh 'yarn add --dev typescript @types/react'
            }
        }

        stage('Build') {
            steps {
                sh 'yarn build'
            }
        }

        stage('Run App') {
            steps {
                sh 'yarn start'
            }
        }
    }

    post {
        failure {
            echo '❌ Something went wrong.'
        }
    }
}
