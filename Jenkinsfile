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
  
  stage("Quality Gate"){
  timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
    def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
    if (qg.status != 'OK') {
      error "Pipeline aborted due to quality gate failure: ${qg.status}"
    }
  }
}
  
}

