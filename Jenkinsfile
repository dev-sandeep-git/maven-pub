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
                git branch: "${params.BRANCH}", url: 'https://your-git-repo-url/project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'nexus-credentials', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASS')]) {
                    sh '''
                        mvn deploy \
                        -DskipTests \
                        -Dnexus.username=$NEXUS_USER \
                        -Dnexus.password=$NEXUS_PASS
                    '''
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
