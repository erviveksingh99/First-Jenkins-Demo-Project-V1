pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps { checkout scm }
        }

        stage('Validate') {
            steps {
                bat 'if not exist demo.html exit 1'
                echo 'demo.html found'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                if not exist C:\\jenkins-deploy\\html-demo mkdir C:\\jenkins-deploy\\html-demo
                copy /Y demo.html C:\\jenkins-deploy\\html-demo\\demo.html
                '''
            }
        }
    }

    post {
        success { echo 'Deploy successful!' }
        failure { echo 'Build failed' }
    }
}