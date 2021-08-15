pipeline {
  agent any
  environment {
    AWS_ECR_REGION = 'us-east-2'
    AWS_ECR_URL = '097816535043.dkr.ecr.us-east-2.amazonaws.com'
  }
  docker.withRegistry(${env.AWS_ECR_URL})
  stages {
    stage('Build') {
      steps {
        sh 'gradlew build bootJar'
        def app = docker.build "healthcheck:${env.BUILD_TAG}"
        app.push()
      }
    }

  }
  
}
