pipeline {
  agent {
    label 'jenkinslave'
  }
  environment {
    AWS_ECR_REGION = 'us-east-2'
    AWS_ECR_URL = '097816535043.dkr.ecr.us-east-2.amazonaws.com'
  }
  stages {
    stage('Build') {
      steps {
        sh 'pwd'
        sh 'gradlew build bootJar'
        echo 'Build Docker image ${GIT_COMMIT}'
      }
    }
  }
  
}
