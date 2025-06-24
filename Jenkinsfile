pipeline {
    agent any

    // Jenkins automatically checks out the repo (from the branch that triggered the build)

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Example: run Maven build if it’s a Maven project
                // sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example: run tests
                // sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add your deploy commands here
            }
        }
    }
}
