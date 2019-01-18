pipeline{
	agent none
	
	stages{
		stage('Pipeline'){
			parallel{
			    stage('iOS'){
				agent { label 'MAC_Agent' }
				stage('Git'){
				    steps{
					echo "Executed on ---- ${NODE_NAME}"
				    }
				}
			    }
			    stage('Android'){
				agent any
				stage('Git'){
				    steps{
					echo "Executed on ---- ${NODE_NAME}"
				    }
				}
			    }
			}	
		}
	}
}
