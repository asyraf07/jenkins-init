pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                git url: "https://github.com/polyglot-devs/todo-api"
            }
        }
        stage('Test') {
            steps {
                script{
                    sh './mvnw test'
                }
            }
        }
        stage('Build project') {
            steps {
                script {
                    sh './mvnw package'
                    sh 'docker build -t asyraf07/book .'
                    sh 'docker push asyraf07/book'
                }
            }
        }
    }
}
