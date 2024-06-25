pipeline {
    agent {
        docker { 
            image 'cypress/base'
            args '-u root:root'
        }
    }

    options {
        skipDefaultCheckout(true)
    }

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
    }

    stages {
        stage('Git checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install dependencies') {
            environment {
                CYPRESS_RECORD_KEY = "a4b7a65f-8f87-4f44-8783-a8e0611a702a"
        }
            steps {
                sh 'npm i'
                sh "npm run test:ci:record"
            }
        }
        stage('Test') {
            steps {
                sh 'npm run test'
            }
        }
    }
}