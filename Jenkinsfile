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

        stage('Debug') {
            steps {
                sh 'echo WORKSPACE CONTENTS: && ls -l && echo MODULE-A CONTENTS: && ls -l module-a || echo "module-a not found"'
            }
        }

        stage('Build and Deploy') {
            parallel {
                stage('Module A') {
                    steps {
                        sh 'mvn clean deploy -pl module-a -am --settings /var/lib/jenkins/.m2/settings.xml'
                    }
                }

                stage('Module B') {
                    steps {
                        sh 'mvn clean deploy -pl module-b -am --settings /var/lib/jenkins/.m2/settings.xml'
                    }
                }

                stage('Module C') {
                    steps {
                        sh 'mvn clean deploy -pl module-c -am --settings /var/lib/jenkins/.m2/settings.xml'
                    }
                }
            }
        }
    }
}
