node {	
  stage('SCM') {
    git 'https://github.com/Rui77/accT'
  } 
  stage('SonarQube analysis') {
	withMaven(maven: 'Maven 3.5.2') {
      withSonarQubeEnv('ADOP Sonar') {		
			sh 'mvn clean package sonar:sonar'
		} // SonarQube taskId is automatically attached to the pipeline context
	}  
  }
}




