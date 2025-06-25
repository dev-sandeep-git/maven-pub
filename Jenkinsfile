pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'Maven'  // Name of your Maven tool in Jenkins
        PATH = "${MAVEN_HOME}/bin:${env.PATH}"
    }

    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Git branch to build')
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/dev-sandeep-git/maven-pub.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Deploy to Nexus') {
    steps {
        sh 'mvn deploy -DskipTests'
    }
}
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
