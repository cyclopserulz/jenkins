pipeline {
    agent any
    environment {
        SONAR_SCANNER_HOME = '/opt/sonar-scanner'
        PATH = "${SONAR_SCANNER_HOME}/bin:${env.PATH}"
    }
    stages {
        stage('Checkout') {
            steps {
                // Your checkout steps here
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                // Your build steps here
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    // Execute the sonar-scanner command
                    sh 'sonar-scanner -Dsonar.projectKey=test-project -Dsonar.sources=src -Dsonar.host.url=http://sonarqube:9000'
                }
            }
        }
        stage('Quality Gate') {
            steps {
                // Your quality gate steps here
            }
        }
    }
}
