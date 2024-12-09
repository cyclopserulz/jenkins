pipeline {
    agent any

    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage("Build") {
            steps {
                sh "javac src/main/java/com/example/*.java"
            }
        }
        stage("SonarQube Analysis") {
            steps {
                withSonarQubeEnv("SonarQube") {
                    sh "whoami"
                    sh "sonar-scanner -Dsonar.projectKey=test-project -Dsonar.sources=src/main/java -Dsonar.host.url=http://sonarqube:9000"
                }
            }
        }
        stage("Test") {
            steps {
                sh "java -cp src/main/java org.junit.runner.JUnitCore com.example.HelloWorldTest"
            }
        }
    }
}
