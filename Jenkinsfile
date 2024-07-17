pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('Clone repository') {
            steps {
                git url: "https://github.com/polyglot-devs/todo-api.git"
            }
        }
        stage('Test') {
            steps {
                dir('todo-api') {
                    sh 'mvn clean test'
                }
            }
        }
        stage('Build project') {
            steps {
                dir('todo-api') {
                    script {
                        sh 'mvn clean package'
                        sh 'docker build -t asyraf07/book .'
                        sh 'docker push asyraf07/book'
                    }
                }
            }
        }
    }
}
