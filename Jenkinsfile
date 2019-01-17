pipeline{
	agent none
	
	stages{
		stage('SCM') {
				agent any
				steps{
					git 'https://github.com/ricardo-softinsa/agent.git'
					echo "Executed on:  ${NODE_NAME}"
				}
		}
		stage("Build Project"){
			parallel {
				stage("iOS Build"){
					agent { label 'MAC_Agent' }
					steps{
						echo "Build Step for iOS"
						echo "Executed on: ${NODE_NAME}"
						//Navigate to project folder (Note: it's where the <Name>.xcodeproj resides)
						//The command below will list all schemes, we then need to choose one
						//COMMAND: sh 'xcodebuild -list -project <NAME>.xcodeproj/'
						//We then choose a scheme and we run it
						//COMMAND: sh 'xcodebuild -scheme <SCHEME_NAME> build'
					}
				}
				stage("Android Build"){
					agent any
					steps{
						echo "Build Step for Android"
						echo "Executed on: ${NODE_NAME}"
						//Navigate to project folder
						//COMMAND: bat 'gradlew [PROJECT_NAME]'
					}
				}
			}
		}
		//uguyguy9gtgyuguygyu
		stage("Distribution"){
			parallel{
				stage("iOS Distribution"){
					agent { label 'MAC_Agent' }
					steps{
						echo "Distribution for iOS"
						echo "Executed on: ${NODE_NAME}"
					}
				}
				stage("Android Distribution"){
					agent any
					steps{
						echo "Distribution for Android"
						echo "Executed on: ${NODE_NAME}"
					}
				}
			}
		}
	}
}
