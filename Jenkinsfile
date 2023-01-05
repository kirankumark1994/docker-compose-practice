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
                    //withCredentials([sshUserPrivateKey(credentialsId: 'docker-machine-ssh-key', keyFileVariable: 'docker-ubuntu', usernameVariable: 'ubuntu')]) {
                      sh(script:"ssh  ubuntu@18.205.158.137 \"mkdir -p /home/ubuntu/compose-deployment/ \" ")
                      sh(script:"scp -r ${WORKSPACE}/* ubuntu@18.205.158.137:/home/ubuntu/compose-deployment/ ")
                      sh(script:"ssh  ubuntu@18.205.158.137 \"cd /home/ubuntu/compose-deployment/ && sudo docker-compose up -d \" ")
                //}
                
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
