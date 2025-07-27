pipeline {
    agent any

    environment {
        PROJECT_DIR = 'frontend' // or '.' if no subfolder
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/hafiz-syed-burhan/nextflix.git'
            }
        }

        stage('Install Dependencies + TypeScript') {
            steps {
                dir("${PROJECT_DIR}") {
                    sh '''
                        yarn install
                        yarn add --dev typescript @types/react
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                dir("${PROJECT_DIR}") {
                    sh '''
                        rm -rf .next
                        yarn build
                    '''
                }
            }
        }

        stage('Run App') {
            steps {
                dir("${PROJECT_DIR}") {
                    sh 'yarn start &'
                }
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
