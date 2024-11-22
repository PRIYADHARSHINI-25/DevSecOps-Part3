pipeline {
  agent any
  tools { 
        maven 'Maven_3_2_5'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=devops-sonar-priya_devsecops -Dsonar.organization=devops-sonar-priya -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=51804ce25c34b7240b58a5c8a4fd31e2744b3f8e'
			}
        } 

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
