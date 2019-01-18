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
                                echo "${UNKNOWN_VAR}"
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
                            slackSend color: 'good', message: "ANDROID\nStatus: Success!\nName: ${currentBuild.fullDisplayName}\nInfo: ${env.BUILD_URL}"
                        }
                        failure{
                            slackSend color: 'danger', message: "ANDROID\nStatus: Failed\nName: ${currentBuild.fullDisplayName}\nInfo: ${env.BUILD_URL}"
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
                            slackSend color: 'good', message: "iOS\nStatus: Success!\nName: ${currentBuild.fullDisplayName}\nInfo: ${env.BUILD_URL}"
                        }
                        failure{
                            slackSend color: 'danger', message: "iOS\nStatus: Failed\nName: ${currentBuild.fullDisplayName}\nInfo: ${env.BUILD_URL}"
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
