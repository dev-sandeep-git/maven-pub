pipeline {
    agent any

    tools {
        maven 'Maven3'  // Your Jenkins Maven config name
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Deploy') {
            steps {
                sh 'mvn clean deploy --settings /var/lib/jenkins/.m2/settings.xml'
            }
        }
    }
}
