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
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                mvn deploy -DskipTests -s /var/lib/jenkins/.m2/settings.xml



            }
        }
    }
}
