pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'gradle build'
      }
    }

  }
  environment {
    AWS_ECR_REGION = 'us-east-2'
    AWS_ECR_URL = '097816535043.dkr.ecr.us-east-2.amazonaws.com'
  }
}