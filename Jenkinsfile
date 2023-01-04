pipeline{
    agent{
        label any 
    }
    stages{
        stage("Checkout"){
            steps{
                echo "======== Executing Checkout========"
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
