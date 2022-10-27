currentBuild.displayName = "todo-app-be-#"+currentBuild.number
pipeline {
    agent any

    stages {
        stage('Build stage') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipelines -t image-build:$BUILD_NUMBER --target builder .'
            }
        }
        stage('Delivery stage') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -f Dockerfile-pipelines -t firestore/todo-be:$BUILD_NUMBER --target delivery .'
            }
        }
          stage('Push Artifact') {
              withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerPwd')]) {
                  sh "docker login -u firestore -p ${dockerPwd}"
        }
                sh "docker push firestore/todo-be:$BUILD_NUMBER"
        }
    }
}
