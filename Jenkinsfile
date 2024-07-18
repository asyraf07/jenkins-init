pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('Clone repository') {
            steps {
                //git url: "https://github.com/polyglot-devs/todo-api.git"
                sh 'rm -rf todo-api'
                sh 'git clone https://github.com/polyglot-devs/todo-api.git'
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
                        sh 'chmod +x ./mvnw'
                    }
                }
            }
        }
        stage('Build image') {
            steps {
                dir('todo-api') {
                    script {
                        //sh 'docker build -t asyraf07/book .'
                        //sh 'docker push asyraf07/book'
                        docker.build("asyraf07/book")
                        docker.withRegistry("https://hub.docker.com/r/asyraf07/book", "dhub") {
                            docker.image("asyraf07/book").push()
                        }
                    }
                }
            }
        }
    }
}
