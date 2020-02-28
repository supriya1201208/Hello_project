pipeline {
    
    agent any

    environment
    {
        PATH="/opt/apache-maven-3.6.3/bin:$PATH"
    }
	
    stages {
    	stage('GIT checkout'){
		steps{
			checkout changelog: false, poll: false, 
			scm: [$class: 'GitSCM', branches: [[name: '*/master']], 
			doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/supriya1201208/Hello_project.git']]]
		}
	}
		
	stage('build && SonarQube analysis') {

		steps {
			echo 'This is a minimal pipeline.'
			sh 'mvn clean package sonar:sonar mvn sonar:sonar -Dsonar.projectKey=supriya_project -Dsonar.host.url=http://18.139.223.23:9000/sonar -Dsonar.login=164cd07afb237247ba16af02373c140f54b8aaf4'
		}
	}
    }	    
}
