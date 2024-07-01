pipeline {
	agent any 
	tools {
		jdk 'jdk16'
		maven 'maven3'
	}
	stages {
		stage ('Git Checkout') {
			steps {
				git branch: 'main', changelog: false, credentialsId: '703e2c04-f024-4318-8f36-648d4ca77b63', poll: false, url: 'https://github.com/Shreyank031/Ekart'
			}
		}
	stage('OWASP Dependency-Check Vulnerabilities') {
		steps {
			dependencyCheck additionalArguments: ''' 
	                    -o './'
	                    -s './'
	                    -f 'ALL' 
	                    --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			    dependencyCheckPublisher pattern: 'dependency-check-report.xml'
      }
    }
		stage ('Compile') {
			steps {
				sh "mvn clean compile -DskipTests=true"
			}
		}
	}
}
