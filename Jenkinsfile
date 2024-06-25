pipeline {
    agent {
        docker { 
            image 'node'
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
            steps {
                sh 'npm i'
            }
        }
        stage('Test') {
            steps {
                sh 'npm run test'
            }
        }
    }
}