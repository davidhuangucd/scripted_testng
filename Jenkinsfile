pipeline {
 agent none
 tools {
    	maven 'Maven'
 }
 stages {
  stage("Checkout"){
   agent any
   when {
					branch 'multibranch'
				}
   steps{
     checkout scm
     //sh 'mvn clean test'
   }
   
  }
  
  stage("Tests") {
   agent any
   when {
					branch 'multibranch'
				}
   steps {
    checkout scm
    sh 'mvn clean test'
    step([$class: 'Publisher', reportFilenamePattern: '**/testng-results.xml'])
   }
  }
  stage('Deploy'){
   when {
					branch 'multibranch'
				}
   agent any
   steps{
     snDevOpsChange()
   }
  }
 }
}
