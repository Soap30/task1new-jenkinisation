pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '''
                docker build -t soap30/task1newjenk .
                docker build -t soap30/task1new-nginx nginx
                '''
            }

        }
        stage('Push') {
            steps {
                sh '''
                docker push soap30/task1newjenk
                docker push soap30/task1new-nginx
                '''
            }

        }
        stage('Deploy') {
            steps {
                sh '''
                ssh jenkins@lorra-deploy <<EOF
                docker network rm task1new-net && echo "removed network" || echo "network already removed"
                docker network create task1new-net
                docker stop nginx && echo "Stopped nginx" || echo "nginx is not running"
                docker rm nginx && echo "removed nginx" || echo "nginx does not exist"
                docker stop flask-app && echo "Stopped flask-app" || echo "flask-app is not running"
                docker rm flask-apptask1 && echo "removed flask-app" || echo "flask-app does not exist"
                docker run -d --name flask-app --network task1new-net soap30/task1newjenk   
                docker run -d --name nginx --network task1new-net -p 80:80 soap30/task1new-nginx
                '''
            }

        }

    }

}