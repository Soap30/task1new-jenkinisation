pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '''
                docker build -t soap30/task1newjenk .
                '''
            }

        }
        stage('Push') {
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