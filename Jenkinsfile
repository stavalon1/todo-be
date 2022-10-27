currentBuild.displayName = "todo-app-be-#"+currentBuild.number
pipeline {
    agent any

    stages {
        stage('Build stage') {
            steps {
              sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipelines -t firestore/todo-be:latest --target builder .'
            }
        }
        stage('Delivery stage') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipelines -t firestore/todo-be:latest --target delivery .'
            }
        }
    }
}
