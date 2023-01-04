pipeline{
    agent any 
    
    parameters {
      string defaultValue: 'master', description: 'Provide branch name ', name: 'BRANCH', trim: true
    }

    stages{
        stage("Checkout"){
            steps{
                echo "======== Executing Checkout========"
                script {
                    sh(script:"git checkout ${BRANCH} ")
                }

            }
        }
        stage("Deploy"){
            steps{
                echo "======== Executing Deploy========"
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: 'docker-machine-ssh-key', keyFileVariable: 'docker-ubuntu', usernameVariable: 'ubuntu')]) {
                      sh(script:"ssh -i ${docker-ubuntu} ubuntu@44.204.237.66  \" date \" ")
                     }
                }
                
            }
        } 
        stage("Status"){
            steps{
                echo "========Checking Status of Deployment========"
            }
        }                
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
