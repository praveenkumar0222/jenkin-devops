pipeline{
	//agent any
	//agent{docker{ image 'maven:3.8.6'}}
	agent{docker{ image 'node:13.8'}}
	stages {
		stage ('Build') {
			steps {
				//sh 'mvn --version'
				sh 'node --version'
				echo "Build"
			}
		}
	
		stage ('Test') {
			steps {
				echo "Test"
			}
		}
		stage ('ntergration Test') {
			steps {
				echo "Intergration Test"
			}
		}
	
	}
	
	post{
		always {
			echo 'Im awesome. I run always'
		}
		success {
			echo 'I run when you are successful'
		}
		failure {
			echo 'I run when you fail'
		}
	}
}
