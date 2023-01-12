pipeline {
    agent { label 'main' }
    

    tools {
        maven '3.6.3' 
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Tajamul-7/devops-automation.git']])               
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t javatechie/devops-integration .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                  withCredentials([string(credentialsId: 'java-techie', variable: 'dockerhubpwd')]) {
   
}

                   sh 'docker push javatechie/devops-integration'
                }
            }
        }
    }
}    
