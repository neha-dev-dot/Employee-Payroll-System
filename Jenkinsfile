pipeline {
    agent any

    stages {
        stage('Install Maven') {
            steps {
                script {
                    sh 'apt-get update && apt-get install -y maven'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'mvn install'
                }
            }
        }

        stage('Run the App') {
            steps {
                script {
                    sh 'nohup mvn spring-boot:run &'
                    sleep 5
                }
            }
        }

        stage('Visit /health route') {
            steps {
                script {
                    sh 'curl http://localhost:8080/health'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    sh 'pkill -f "java"'
                }
            }
        }
    }
}
