pipeline {
	agent any
	stages{
		stage('Build'){
			steps{
				echo "Build"
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
	} post {
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
