pipeline{
	agent any
	tools {
			maven 'maven3'
          }
	
	stages{
	stage('maven build/package'){
		steps{
			sh 'mvn clean package'
		}
		}
	}
}
