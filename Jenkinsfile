pipeline {
    agent any // running our application and our builds

// environments {
//     KEY = Value
// }
    stages {
        stage ('Build Frontend') {
            steps {
                sh "echo Building Frontend"
                sh "cd frontend && npm install && npm run build"
            }
        }

        // stage ('Test') {
        //     steps {
        //         sh "echo Testing Stage 2"
        //     }
        // }
        // stage ('testGitWebhook') {
        //     steps {
        //         sh "echo It works now!"
        //     }
        // }

        // stage ('Deploy') {
        //     steps {
        //         sh "echo Deploying Stage 3"
        //     }
        // }
    }
}