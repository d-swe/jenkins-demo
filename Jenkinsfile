pipeline {
    agent any // running our application and our builds

// environments {
//     KEY = Value
// }
    stages {
        stage('Build Frontend') {
            steps {
                sh "echo Building Frontend"
                sh "cd frontend && npm install && npm run build"
            }
        }
        stage('Deploy Frontend'){
            steps{
                script{
                    try {
                      withAWS(region: 'us-east-2', credentials: 'AWS_CREDENTIALS'){
                        sh "aws s3 sync frontend/dist s3://candy-inventory-management" 
                        }catch (Exception e) {
                            echo "${e}"
                            throw e
                        }   
                    }
                }
            }
        }
        stage('Build Backend') {
            steps {
                sh "cd demo && mvn clean install"
            }
        }
        stage('Test Backend'){
            steps{
                sh "cd demo && mvn test"
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