pipeline {
	agent any
	//agent { docker { image 'maven:3.8.4'} }
	//agent { docker { image 'node:17.4.0'} }

	stages{
		stage('Build'){
			steps{
				//sh 'mvn --version'	
				//sh 'node --version'				
				echo "Build"
				echo "PATH-$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOb_NAME - $env.JOb_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Test'){
			steps{
				echo "Test"
			}
		}
		stage('Integraion Test'){
			steps{
				echo "Integraion Test"
			}
		}
	} 
	post {
		always {
			echo 'im awesome ,i always run'
		}
		success {
			echo 'I run when youre are success'
		}
		failure {
			echo 'I run when you fail'
		}
	}

}
