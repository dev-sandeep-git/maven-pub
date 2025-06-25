pipeline {
    agent any

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
