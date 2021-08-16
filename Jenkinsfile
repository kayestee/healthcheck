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
		docker.withRegistry('${env.AWS_ECR_URL}','5dd9b7e7-63e3-477f-9ad2-18bd9baa8dec'){
			def app = docker.build("healthcheck:${GIT_COMMIT}")		  
			app.push('latest') 
		}
	}
    	}
    }
  }
  
}
	
