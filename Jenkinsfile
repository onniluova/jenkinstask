
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/onniluova/jenkinstask.git'
            }
        }

        stage('Build') {
            steps {
                tool 'Maven'
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            jacoco execPattern: '**/target/jacoco.exec'
        }
    }
}

