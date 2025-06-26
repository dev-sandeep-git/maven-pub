pipeline {
    agent any

    tools {
        maven 'maven'  // Your Jenkins Maven config name
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Deploy') {
            parallel {
                stage('Module A') {
                    steps {
                        sh 'mvn clean deploy -pl module-a --settings /var/lib/jenkins/.m2/settings.xml'
                    }
                }

                stage('Module B') {
                    steps {
                        sh 'mvn clean deploy -pl module-b --settings /var/lib/jenkins/.m2/settings.xml'
                    }
                }

                stage('Module C') {
                    steps {
                        sh 'mvn clean deploy -pl module-c --settings /var/lib/jenkins/.m2/settings.xml'
                    }
                }
            }
        }
    }
}
