pipeline{
	  stage('com'){
    def mvnHome = tool name: 'Apache Maven 3.8.5', type: 'maven'
    sh "${mvnHome}/bin/mvn -B -DskipTests clean package"
  }
	agent any
	//agent{docker{ image 'maven:3.8.6'}}
	//agent{docker{ image 'node:13.8'}}
	environment {
		dockerHome= tool 'mydocker'
		mavenHome= tool 'maven-3.8.5'
		PATH="$dockerHome/bin:mavenHome/bin:$PATH"
	}

	stages {
		stage ('Build') {
			steps {
				sh 'docker version'
				echo "Build"
				echo"PATH - $PATH"
				echo"BUILD_NUMBER - $env.BUILD_NUMBER"
				echo"BUILD_ID - $env.BUILD_ID"
				echo"JOB_NAME - $env.JOB_NAME"
				echo"BUILD_TAG - $env.BUILD_TAG"
				echo"BUILD_URL - $env.BUILD_URL"

			}
		}

		stage('compile') {
			steps {
				sh "mvn clean compile"
			}
		}
	
		stage ('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage ('Intergration Test') {
			steps {
				echo "mvn failesafe:integration-test failsafe:verify"
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
