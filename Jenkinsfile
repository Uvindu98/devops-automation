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
                    bat 'docker build -t myapp .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                  
                   bat 'docker login -u uvindu098 -p dckr_pat_8o5QucdDayIPdLR5lvFA86cMHIc'
                   bat 'docker tag myapp uvindu098/devops-integration:myapp'
                   bat 'docker push uvindu098/devops-integration:myapp'
                }
            }
        }
        
    }
}
