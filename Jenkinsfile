pipeline{
	agent none
	
	stages{
        stage('Pipeline'){
            parallel{
                stage('Android'){
                    agent any
                    stages{
                        stage('Git Checkout'){
                            steps{
                                echo "Checking out git repo on ---- ${NODE_NAME}"
                            }
                        }
                        stage('Analising code'){
                            steps{
                                echo "Analising code on ---- ${NODE_NAME}"
                            }
                        }
                        stage('Deploying'){
                            steps{
                                echo "Deploying code on ---- ${NODE_NAME}"
                            }
                        }
                    }
                    post{
                        success{
                            slackSend color: 'good', message: "Platform: ANDROID\nStatus: Success!\nName: ${currentBuild.fullDisplayName}"
                        }
                        failure{
                            slackSend color: 'danger', message: "Platform: ANDROID\nStatus: Failed\nName: ${currentBuild.fullDisplayName}"
                        }
                    }
                }
                stage('iOS'){
                    agent{
                        label 'MAC_Agent'
                    }
                    stages{
                        stage('Git Checkout'){
                            steps{
                                echo "Checking out git repo on ---- ${NODE_NAME}"
				    echo "${VARR}"
                            }
                        }
                        stage('Analising code'){
                            steps{
                                echo "Analising code on ---- ${NODE_NAME}"
                            }
                        }
                        stage('Deploying'){
                            steps{
                                echo "Deploying code on ---- ${NODE_NAME} !!!!!!!!!!!!!!!!!!!!!"
                            }
                        }
                    }
                    post{
                        success{
                            slackSend color: 'good', message: "Platform: iOS\nStatus: Success!\nName: ${currentBuild.fullDisplayName}"
                        }
                        failure{
                            slackSend color: 'danger', message: "Platform: iOS\nStatus: Failed\nName: ${currentBuild.fullDisplayName}"
                        }
                    }
                }
            }
        }
    }
    post{
        success{
            slackSend color: 'good', message: "Name: ${currentBuild.fullDisplayName}\nStatus: Success!\nInfo: ${env.BUILD_URL}"
        }
        failure{
            slackSend color: 'danger', message: "Name: ${currentBuild.fullDisplayName}\nStatus: Failure\nInfo: ${env.BUILD_URL}"
        }
    }
}

