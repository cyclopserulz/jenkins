pipeline {
    agent any
    environment {
        SONAR_SCANNER_HOME = '/opt/sonar-scanner'
        PATH = "${SONAR_SCANNER_HOME}/bin:${env.PATH}"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm // Checkout source code
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                // Your build commands here
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'sonar-scanner -Dsonar.projectKey=test-project -Dsonar.sources=src -Dsonar.host.url=http://sonarqube:9000'
                }
            }
        }
        stage('Quality Gate') {
            steps {
                echo 'Checking quality gate...'
                // Implement your quality gate checking logic here
            }
        }
    }
}
