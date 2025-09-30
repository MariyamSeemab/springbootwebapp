pipeline {
    agent any

    tools {
        maven 'Maven 3.6'
        snyk 'Snyk CLI'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Use 'bat' for Windows Jenkins agents; use 'sh' for Linux agents
                bat 'mvn clean install'
            }
        }

        stage('Snyk Security Scan') {
            steps {
                snykSecurity failOnIssues: true, snykTokenId: 'snyk-api-token'
            }
        }
    }
}
