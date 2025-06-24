pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout private GitHub repo using HTTPS and PAT
                git(
                    url: 'https://github.com/dev-sandeep-git/maven-pub.git/',
                    credentialsId: 'github-pat'
                )
            }
        }
    }
}
