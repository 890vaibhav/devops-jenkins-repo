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
				echo "BUILD_TAG - $env.BUILD_TAG"
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
			stage ('Build Docker Image'){
				//"docker build -t vaccine89/currency-exchange:$env.BUILD.TAG"
				script {
					dockerImage = docker.build("vaccine89/currency-exchange:$env.BUILD.TAG")
				}
			}
			stage ('Push Docker Image') {
				steps {
					script {
						docker.withRegistry('', 'dockerHub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}

			stage ('Package') {
				steps {
					sh 'mvn package -DskipTests'
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
