pipeline {
    agent any
    /*environment {
        PR_BUILD = (env.CHANGE_ID != null)  // Example: setting a custom environment variable
    }

    stages {

        stage('Build') {
            steps {
                script {
                    if (PR_BUILD) {
                        echo "Building Pull Request #${env.CHANGE_ID}"
                        // Add custom build logic for PRs
                    } else {
                        echo "Building Branch: ${env.BRANCH_NAME}"
                        // Add logic for regular branch builds
                    }
                }
            }
        }
*/        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Unit Testing') {
            steps {
                sh """
                echo "Running Unit Tests"
                """
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
