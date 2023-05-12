pipeline {
    agent any
    tools{
        maven '3.9.2'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Uvindu98/devops-automation.git']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t Uvindu98/devops-integration .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'dckrhub', variable: 'dockerhub')]) {
                   sh 'docker login -u uvindu098 -p ${dockerhub}'

}
                   sh 'docker push Uvindu98/devops-integration'
                }
            }
        }
        
    }
}