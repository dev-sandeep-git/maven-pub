pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                // your deploy script here
                sh 'mvn deploy -DskipTests'
            }
        }
    }  // closes stages

}  // closes pipeline
