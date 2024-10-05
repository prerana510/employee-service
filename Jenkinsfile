pipeline {
	agent any tools {
		maven 'my-maven'
		jdk 'my-jdk'
	}
	stages {
		stage('Clone') {
			steps {git url:'https://github.com/prerana510/employee-service.git',branch:'main'}
		}
		stage('Build') {
			step {bat "mvn clean install -DskipTests"}
		}
		stage('Test') {
			steps {bat "mvn test"}
		}
    stage('Deploy') {
			steps {bat "docker build -t employee-image ." 
             bat "docker run -p 8082:8082 -d -name employee-container employee-image"}
		}
	}
}
