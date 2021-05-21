pipeline {
    agent any
    tools {
        maven 'maven-3.6.3'
    }

    stages {
        stage('Build') {
            steps {
                sh  'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                script {
			deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://localhost:8081')], contextPath: '/mavenpipeline1', war: 'target/*.war'
                }
            }  
        }      
	}
}
