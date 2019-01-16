pipeline{
	agent none
	
	stages{
		stage('SCM') {
				agent any
				steps{
					git 'https://github.com/ricardo-softinsa/Node-Pipeline.git'
				}
		}
		stage("Build Project"){
			parallel {
				stage("iOS Build"){
					agent { label 'MAC_Agent' }
					steps{
						echo "Build Step for iOS"
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
						//Navigate to project folder
						//COMMAND: bat 'gradlew [PROJECT_NAME]'
					}
				}
			}
		}
		//For this stage we need to download testfairy-uploader.sh (From command-line-uploader project TestFairy GitHub)
		stage("TestFairy Distribution"){
			parallel{
				stage("iOS Distribution"){
					agent { label 'MAC_Machine' }
					steps{
						echo "Distribution for iOS"
						//sh 'testfairy-uploader.sh [PROJECT_APK]'
					}
				}
				stage("Android Distribution"){
					agent any
					steps{
						echo "Distribution for Android"
						//sh 'testfairy-uploader.sh [PROJECT_APK]'
					}
				}
			}
		}
	}
}
