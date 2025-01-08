pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Unit Testing') {
            steps {
                sh '''
                echo "Running Unit Tests"
                '''
            }
        }

        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Deploy To Dev & QA') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "Building Artifact for Dev Environment"
                """
                sh """
                echo "Deploying to Dev Environment"
                """
                sh """
                echo "Deploying to QA Environment"
                """
            }
        }

        stage('Deploy To Staging and Pre-Prod Code') {
            when {
                branch 'main'
            }
            steps {
                sh """
                echo "Building Artifact for Staging and Pre-Prod Environments"
                """
                sh """
                echo "Deploying to Staging Environment"
                """
                sh """
                echo "Deploying to Pre-Prod Environment"
                """
            }
        }
    }
}
