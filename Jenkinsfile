#!groovy
pipeline{
	agent any
	stages {
		stage ('suresh build'){
			when{
				branch 'suresh'
			}
			steps{
			sh 'mvn clean install'
			}
		}
		stage ('master build'){
			when {
				branch 'master'
			}
			steps{
			sh 'mvn clean install'
			}
		}
	}
}
