pipeline{
	agent none
	
	stages{
		stage('Pipeline'){
			parallel{
			    stage('iOS'){
				    agent { label 'MAC_Agent' }
				    steps{
					echo "Executed on ---- ${NODE_NAME}"
					    stage("Teste"){
						    steps{
							echo "Somethiiiingggggggggggg"  
						    }
					    }
				    }
			    }
			    stage('Android'){
				    agent any
				    steps{
					echo "Executed on ---- ${NODE_NAME}"
				    }
			    }
			}	
		}
	}
}
