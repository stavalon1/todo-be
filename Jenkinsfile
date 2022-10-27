currentBuild.displayName = "todo-app-be-#"+currentBuild.number
pipeline {
    agent any
    
    environment{
        TAG = currentBuild.number
    }

    stages {
        stage('Build stage') {
            steps {
              sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipelines -t firestore/todo-be:$TAG --target builder .'
            }
        }
        stage('Delivery stage') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipelines -t firestore/todo-be:$TAG --target delivery .'
            }
        }
    }
}
