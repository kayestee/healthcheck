pipeline {
  agent {
    label 'jenkinslave'
  }
  environment {
    AWS_ECR_REGION = 'us-east-2'
    AWS_ECR_URL = 'https://097816535043.dkr.ecr.us-east-2.amazonaws.com'
    AWS_ECR_CRED = 'ecr:us-east-2:jenkindsecrrole' 
 }
  stages {
    stage('Build') {
      steps {
        sh 'pwd'
        sh 'sh gradlew build bootJar'
	script {
		docker.withRegistry('${env.AWS_ECR_URL}','${env.AWS_ECR_CRED}'){
			def app = docker.build("healthcheck:${GIT_COMMIT}")		  
			app.push('latest') 
		}
	}
    	}
    }
  }
  
}
	
