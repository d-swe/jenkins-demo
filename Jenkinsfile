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
                    }
                    }catch (Exception e) {
                            echo "${e}"
                            throw e
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
        stage('Deploy Backend'){
            steps{
                try {
                      withAWS(region: 'us-east-1', credentials: 'AWS_CREDENTIALS'){
                        sh "aws s3 sync demo/target/*.jar s3://bjgomes-bucket-sdet-backend"
                        sh "aws elasticbeanstalk create-application-version --application-name myName --version-label 0.0.1 --source-bundle S3Bucket="bjgomes-bucket-sdet-backend",S3Key="*.jar""
                        sh "aws elasticbeanstalk update-environment --environment-name myName --version-label 0.0.1"
                        }catch (Exception e) {
                            echo "${e}"
                            throw e
                        }   
                    }
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