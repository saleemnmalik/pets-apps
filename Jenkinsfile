pipeline{
	agent any
	tools {
			maven 'maven3'
          }
	
	stages{
		stage('Git Chekcout'){
		steps{
			git credentialsId: 'github', url: 'https://github.com/saleemnmalik/pets-apps'
		}
		}
	stage('maven build/package'){
		steps{
			sh 'mvn clean package'
		}
		}
	}
}
