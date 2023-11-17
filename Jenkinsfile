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
                docker run -d -p 80:5500 --name task1 soap30/task1newjenk
                '''
            }

        }

    }

}