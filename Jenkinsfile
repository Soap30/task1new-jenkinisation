pipeline {
    agent any
    environment {
        YOUR_NAME = credentials("YOUR_NAME)
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                docker push soap30/task1newjenk
                '''
            }

        }
        stage('Deploy') {
            steps {
                sh '''
                kubectl apply -f .
                '''
            }

        }

    }

}