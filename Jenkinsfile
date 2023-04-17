pipeline {
	agent any
	stages {
		stage ('Build'){
			steps {
				echo "Build"
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
	} post {
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
