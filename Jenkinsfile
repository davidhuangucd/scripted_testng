pipeline {
 agent none
 tools {
    	maven 'Maven'
 }
 stages {
  stage("Checkout"){
   agent any
   when {
					branch 'dev'
				}
   steps{
     checkout scm
     //sh 'mvn clean test'
   }
   
  }
  
  stage("Tests") {
   agent any
   when {
					branch 'dev'
				}
   steps {
    checkout scm
    sh 'mvn clean test'
    step([$class: 'Publisher', reportFilenamePattern: '**/testng-results.xml'])
   }
  }
  stage('Deploy'){
   when {
					branch 'dev'
				}
   agent any
   steps{
     snDevOpsChange()
   }
  }
 }
}
