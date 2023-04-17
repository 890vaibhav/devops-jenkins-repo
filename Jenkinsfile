pipeline {
	agent any
	// agent {docker {image 'maven:3.6.3'}}

	environment {
		dockerHome = tool 'mydocker'
		mavenHome = tool 'mymaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage ('Checkout'){
			steps {
				// sh 'mvn --version'
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "JOB_NAME - $env.JOB_NAME"
			}
		}
		stage ('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}
			stage ('Test'){
			steps {
				sh  'mvn test'
			}
		}
			stage ('Integration'){
			steps {
				sh 'mvn failsafe:integration-test failsafe:verify'
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
