pipeline {
    agent any
	tools {
		maven 'Maven 3.5.2'
	}
    stages {
		stage('Sonar') {
            steps {
                withSonarQubeEnv('ADOP Sonar') {
					sh 'mvn clean package sonar:sonar'
				}
            }
        }
		stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}