pipeline{
	agent none
	
	stages{
		stage('Pipeline'){
			parallel{
			    stage('iOS'){
				stage('Git'){
				    agent { label 'MAC_Agent' }
				    steps{
					echo "Executed on ---- ${NODE_NAME}"
				    }
				}
			    }
			    stage('Android'){
				stage('Git'){
				    agent any
				    steps{
					echo "Executed on ---- ${NODE_NAME}"
				    }
				}
			    }
			}	
		}
	}
}
