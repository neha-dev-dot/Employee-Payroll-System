pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // If using Maven
                    sh 'mvn install'

                    // If using Gradle
                    // sh './gradlew build'
                }
            }
        }

        stage('Run the App') {
            steps {
                script {
                    // Run the application (example: for Spring Boot)
                    sh 'nohup mvn spring-boot:run &'

                    // If using Gradle, use:
                    // sh './gradlew bootRun &'

                    // Give the app some time to start
                    sleep 5
                }
            }
        }

        stage('Visit /health route') {
            steps {
                script {
                    // Make a request to the health route
                    sh 'curl http://localhost:8080/health'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    // Kill any running Java processes (e.g., Spring Boot app)
                    sh 'pkill -f "java"'
                }
            }
        }
    }
}
