pipeline{

    agent any
    environment{
        DOCKERHUB_USER = "tuanlinhdocker"
        APP_NAME = "demo_cicd"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USER}" + "/" + "${APP_NAME}"
        REGISTRY_CREPS = 'dockerhub'
    }
    
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
        stage('Build Docker Image'){
            steps{
                script{
                    docker_image = docker.build "${IMAGE_NAME}"
                }
            }
        }
        stage('Push Docker Image'){
            steps{
                script{
                    docker.withRegistry('',REGISTRY_CREPS){
                        docker_image.push("$BUILD_NUMBER")
                        docker_image.push("laster")
                    }
                }
            }
        }
    }
        
}