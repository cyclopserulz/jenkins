pipeline {
    agent any

    environment {
        SONAR_SCANNER_HOME = '/opt/sonar-scanner/sonar-scanner-5.0.1.3006-linux/bin'
        PATH = "${env.PATH}:${SONAR_SCANNER_HOME}"
    }

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
                    sh "sonar-scanner -Dsonar.projectKey=test-project -Dsonar.sources=src/main/java -Dsonar.host.url=http://sonarqube:9000"
                }
            }
        }
        stage("Test") {
            steps {
                sh "mvn clean test"
            }
        }
    }
}
