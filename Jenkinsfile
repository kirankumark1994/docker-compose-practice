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
