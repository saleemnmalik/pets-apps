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

	stage('Nexus Deploy'){
		steps{
			scripts{
				def pomFile = readMavenPom file: 'pom.xml'
			    def version = pomFile.version
			    def nexusRepo = version.endsWith('SNAPSHOT') ? "pets-app-snapshot" : "pets-app-release"
			    nexusArtifactUploader artifacts: [[artifactId: 'pets-app', classifier: ' ', file: 'target/pets-app.war', type: 'war']], 
				credentialsId: 'nexus3', 
				groupId: 'in.javahome', 
				nexusUrl: '172.31.4.68:8081',
			    nexusVersion: 'nexus3', 
				protocol: 'http', 
				repository: nexusRepo, 
				version: version
			}
		}
		}

	}
}
