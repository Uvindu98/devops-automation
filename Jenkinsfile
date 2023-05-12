pipeline {
    agent any
    tools{
        maven '3.9.2'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Uvindu98/devops-automation.git']]])
                
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    bat 'docker build -t uvindu98/devops-integration .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'dckrhub', variable: 'dockerhub')]) {
                   bat 'docker login -u uvindu098 -p ${dockerhub}'

}
                   bat 'docker push uvindu98/devops-integration'
                }
            }
        }
        
    }
}