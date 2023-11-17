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
                docker stop task1 && echo "Stopped task1" || echo "task1 is not running"
                docker rm task1 && echo "remove task1" || echo "task1 does not exist"
                docker run -d -p 80:5500 --name task1 soap30/task1newjenk
                '''
            }

        }

    }

}