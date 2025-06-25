pipeline {
    agent any

    tools {
        maven 'maven'  // use the exact name from Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Deploy') {
            steps {
                sh 'mvn clean deploy --settings settings.xml'
            }
        }
    }
}
