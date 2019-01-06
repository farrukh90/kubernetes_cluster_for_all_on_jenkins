pipeline{
    agent any
    parameters { 
        string(name: 'ENVIR', defaultValue: 'dev', description: 'Please enter Env Name')
        string(name: 'ACTION', defaultValue: 'apply', description: 'Please enter apply/destroy ') 

    }
    stages{
        stage("pull Repo"){
            steps{
                git 'https://github.com/farrukh90/terraform.git'
            }
        }
        stage("Initialization"){
            steps{
                ws("${workspace}/${ENVIR}/kubernetes_cluster_private/"){
                    sh "terraform init"
                }
            }
        }
        stage("Creating"){
            steps{
                ws("${workspace}/${ENVIR}/kubernetes_cluster_private/"){
                    sh "echo ${ENVIR} cluster will be created"
                    sh "terraform ${ACTION} -auto-approve"
                }
            }
        }
    }
}
