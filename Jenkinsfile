pipeline {
    agent any

    tools {
        maven 'maven'   
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -X -s /var/lib/jenkins/.m2/settings.xml'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                sh 'mvn deploy -DskipTests -X -s /var/lib/jenkins/.m2/settings.xml'
            }
        }
    }
}
