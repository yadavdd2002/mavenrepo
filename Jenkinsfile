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
	stage ('Notification') {
		//slackSend color: 'good', message: 'Deployment Sucessful'
		emailext (
		      subject: "Job Completed",
		      body: "Jenkins Pipeline Job for Maven Build got completed !!!",
		      to: "yadavdd@gmail.com"
		    )
	}
    }