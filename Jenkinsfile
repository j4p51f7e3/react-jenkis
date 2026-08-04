pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    environment {
        CI = 'true'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/j4p51f7e3/react-jenkis.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'node -v'
                bat 'npm -v'
                bat 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: 'dist/**', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'React build successful!'
        }

        failure {
            echo 'React build failed!'
        }

        always {
            cleanWs()
        }
    }
}