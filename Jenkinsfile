pipeline {
    agent any

	tools {
		maven 'maven3.6'
	}

//	environment {
//		M2_INSTALL = "/home/gamut/Distros/apache-maven-3.6.0/bin/mvn"
//	}

    stages {
		stage('Clone-Repo') {
			steps {
				checkout scm
			}
		}
		stage('Build') {
	    	steps {
				sh 'mvn install -DskipTests'
			}
	    }
		stage('Unit Tests') {
			steps {
				sh 'mvn surefire:test'
			}
		}
		stage('Deployment') {
	    	steps {
				//sh 'sshpass -p "soumya" scp target/gamutkart.war soumya@172.17.0.2:/home/soumya/reddy/apache-tomcat-8.5.42/webapps'
				cp target/gamutkart.war /home/soumya/reddy/apache-tomcat-8.5.42/webapps/
			}
		}
    }
}
