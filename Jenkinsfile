pipeline {
    agent any // running our application and our builds

// environments {
//     KEY = Value
// }
    stages {
        stage ('Build') {
            steps {
                sh "echo Building Stage 1"
            }
        }

        stage ('Test') {
            steps {
                sh "echo Testing Stage 2"
            }
        }
        stage ('testGitWebhook') {
            steps {
                sh "echo It works now!"
            }
        }

        stage ('Deploy') {
            steps {
                sh "echo Deploying Stage 3"
            }
        }
    }
}