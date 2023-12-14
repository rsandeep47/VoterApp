pipeline {
    agent any

    stages {
        stage('CLONE SCM') {
            steps {
                echo 'Cloing code from GITHUB'
				git branch: 'main', url: 'https://github.com/rsandeep47/VoterApp.git'
            }
        }
		 stage('Build artifact') {
            steps {
                echo 'Build artifact using maven'
				sh 'mvn clean install'
            }
        }
		 stage('Deploy') {
            steps {
                echo 'Deploy app to Tomcat Applicaton Server'
				deploy adapters: [tomcat9(credentialsId: 'TomcatCred', path: '', url: 'http://3.91.244.139:8082/')], contextPath: 'VoterApp', war: '**/*.war'
            }
        }
    }
}
