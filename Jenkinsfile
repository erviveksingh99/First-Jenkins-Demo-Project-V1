pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps { checkout scm }
        }

        stage('Validate') {
            steps {
                bat 'if not exist index.html exit 1'
                echo 'index.html found'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                if not exist C:\\jenkins-deploy\\html-demo mkdir C:\\jenkins-deploy\\html-demo
                copy /Y index.html C:\\jenkins-deploy\\html-demo\\index.html
                '''
            }
        }
    }

    post {
        success { echo 'Deploy successful!' }
        failure { echo 'Build failed' }
    }
}