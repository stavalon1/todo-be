currentBuild.displayName = "todo-app-#"+currentBuild.number
pipeline {
    agent any

    stages {
        stage('Build stage') {
            steps {
              sh 'DOCKER_BUILDKIT=1 docker build -t firestore/todo-be:latest --target builder .'
            }
        }
        stage('Delivery stage') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t firestore/todo-be:latest --target delivery .'
            }
        }
    }
}
