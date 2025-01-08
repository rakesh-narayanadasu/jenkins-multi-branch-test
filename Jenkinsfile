pipeline {
    agent any

    // Environment variables for Nexus
    environment {
        NEXUS_URL = 'http://nexus-repo-url'
        NEXUS_REPO = 'maven-releases'
        NEXUS_CREDENTIALS_ID = 'nexus-credentials-id'
    }

    triggers {
        // Trigger pipeline when a pull request is raised or updated
        genericTrigger(
            causeString: 'Triggered by Pull Request',
            genericVariables: [
                [key: 'targetBranch', value: '$.resource.targetBranch']
            ],
            token: 'jenkins-webhook-token',
            printContributedVariables: true,
            printPostContent: true,
            regexpFilterText: '$targetBranch',
            regexpFilterExpression: 'refs/heads/(develop|uat|main)'
        )
    }

    stages {
        stage('Linting and Formatting Checks') {
            steps {
                echo 'Running linting and formatting checks...'
            }
        }

        stage('Build WAR File') {
            steps {
                echo 'Building WAR file...'
            }
        }

        stage('Upload Artifact to Nexus') {
            steps {
                echo 'Uploading WAR file to Nexus repository...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        failure {
            echo 'Pipeline failed!'
        }
        success {
            echo 'Pipeline completed successfully.'
        }
    }
}
