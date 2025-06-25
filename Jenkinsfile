pipeline {
    agent any

    tools {
        maven 'maven'   // Make sure 'maven' is the correct Maven tool name configured in Jenkins global tools
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm   // Checks out your source code from the SCM configured in Jenkins
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -X -s /var/lib/jenkins/.m2/settings.xml' 
                // -X enables debug output, useful for troubleshooting, can remove if verbose not needed
                // Make sure settings.xml path is correct and accessible by Jenkins user
            }
        }

        stage('Deploy to Nexus') {
            steps {
                sh 'mvn deploy -DskipTests -X -s /var/lib/jenkins/.m2/settings.xml' 
                // Skip tests during deploy to speed up pipeline; remove -DskipTests if you want to run tests
            }
        }
    }
}
