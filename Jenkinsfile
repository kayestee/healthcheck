pipeline {
  agent {
    label 'jenkinslave'
  }
  environment {
    AWS_ECR_REGION = 'us-east-2'
    AWS_ECR_URL = 'https://097816535043.dkr.ecr.us-east-2.amazonaws.com'
  }
  stages {
    stage('Build') {
      steps {
        sh 'pwd'
        sh 'sh gradlew build bootJar'
	script {
		docker.withRegistry('${env.AWS_ECR_URL}','3834b8ec-9e15-4a0b-9e1e-3d70af9b4bcf'){
			def app = docker.build("healthcheck:${GIT_COMMIT}")		  
			app.push('latest') 
		}
	}
    	}
    }
  }
  
}
	
