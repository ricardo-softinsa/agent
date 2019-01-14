pipeline{	
	agent none
	stages{
	  stage('SCM') {
		agent any
		steps{
			git 'https://github.com/ricardo-softinsa/agent.git'
		}
	  }
	  stage('First') {
		agent any
		steps{
			echo "First stage executed on ${NODE_NAME}"
		}
	  }
	  stage('Second'){
		agent { label 'ubuntu_agent' }
		steps{
			echo "Second stage executed on ${NODE_NAME}"
		}
	  }
	  stage('Third'){
		agent { label 'ubunu_agent' }
		steps{
			echo "Third stage executed on ${NODE_NAME}"
		}
	  }
	}
}
