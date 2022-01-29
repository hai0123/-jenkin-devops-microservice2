pipeline {
	agent any
	//agent { docker { image 'maven:3.8.4'} }
	//agent { docker { image 'node:17.4.0'} }
	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout') {
			steps{
				sh 'mvn --version'	
				sh 'docker version'				
				echo "Build"
				echo "PATH-$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOb_NAME - $env.JOb_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test') {
			steps{
				sh "mvn test"
			}
		}
		stage('Integraion Test') {
			steps{
				sh  "mvn failsafe:integration-test failsafe:verify "
			}
		}
		stage('Package') {
			steps{
				sh  "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image') {
			steps{
				//docker build -t nagaraju12/jenkin-devop-microservice:$env.BUILD_TAG
				script {
					dockerimage = docker.build("nagaraju12/jenkin-devop-microservice:$env.BUILD_TAG")
				}
		
			}
		}
		stage('Push Docker Image') {
			steps{
				script{
					docker.withRegistry('', 'dockerhub'){
					dockerImage.push();
					dockerImage.push('latest');
					}

				}
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
