pipeline {
	agent any
	// agent {docker {image 'maven:3.6.3'}}
	stages {
		stage ('Build'){
			steps {
				// sh 'mvn --version'
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "JOB_NAME - $env.JOB_NAME"
			}
		}
			stage ('Test'){
			steps {
				echo "Test"
			}
		}
			stage ('Integration'){
			steps {
				echo "Integration"
			}
		}
	} 
	post {
		always {
			echo "Im Awesom,i run always"
		}
		success {
			echo "i Run when you are successful"
		}
		failure {
			echo "I run when you fail"
		}
	}
}
