pipeline {
    agent any // running our application and our builds

// environments {
//     KEY = Value
// }
    stages {
        stage ('Build') {
            steps {
                sh "Building Stage 1"
            }
        }

        stage ('Test') {
            steps {
                sh "Testing Stage 2"
            }
        }

        stage ('Deploy') {
            steps {
                sh "Deploying Stage 3"
            }
        }
    }
}