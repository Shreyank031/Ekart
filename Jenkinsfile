pipeline {
	agent any 
	tools {
		jdk 'jdk22'
		maven 'maven3'
	}
	stages {
		stage ('Git Checkout') {
			steps {
				git branch: 'main', changelog: false, credentialsId: '703e2c04-f024-4318-8f36-648d4ca77b63', poll: false, url: 'https://github.com/Shreyank031/Ekart'
			}
		}
		stage ('Compile') {
			steps {
				sh "mav clean compile -DskipTests=true"
			}
		}
	}
}
