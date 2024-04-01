pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }
	stage('Build') {
		steps {
			sh 'mvn install'
		}
	}	
 
	stage ('Compile'){
	        steps {
			sh 'mvn clean compile'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		deploy adapters: [tomcat9(credentialsId: '1cbc0a58-9677-402b-b9d9-836242251b7a', path: '', url: 'http://18.119.136.174:8081')], contextPath: 'gamutkart', war: '**/*.war'}
    }
}
}
