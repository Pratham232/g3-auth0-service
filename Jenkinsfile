pipeline{
	agent any
	stages{
		stage('Checkout'){
			steps{
				git branch: "main", url: 'https://github.com/Pratham232/g3-auth0-service.git'
			
			}
			
		}
		
		stage('Build'){
			steps{
				sh 'chmod a+x mvnw'
				sh './mvnw clean package -DskipTests=true' 
			}
			
			post{
				always{
					archiveArtifacts 'target/*.jar'
				}
			}
		}
		
		stage(DockerBuild){
			steps{
				sh 'docker build -t itsmepratham23/g3-auth0-service:auth0-service-tag .'
				sh 'docker push itsmepratham23/g3-auth0-service:auth0-service-tag'
			}
		}
		
	}

}