pipeline{

    agent any
    
    stages{
        stage ('Clean The Workspace'){
            steps{
                script{
                    cleanWs()

                }
            }
            
        }
        stage('Check SCM'){
            steps{
                script{
                    git credentailId: "github",
                    url: "https://github.com/hashirama-hub/demo_cicd.git",
                    branch: "main"
                }
            }
        }
    }
        
}