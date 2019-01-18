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
                                echo ${UNKNOWN_VAR}
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
                            echo "Application successfully deployed on Android!!!"
                        }
                        failure{
                            echo "Failed to deploy on Android!!!"
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
                            echo "Application successfully deployed on iOS!!!"
                        }
                        failure{
                            echo "Failed to deploy on iOS!!!"
                        }
                    }
                }
            }
        }
    }
}
