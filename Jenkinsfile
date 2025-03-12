pipeline {
    environment {
    imagename = "backend"
    jenkinsProject = 'calculator-webapp-backend'
  }

    agent any
    stages {

        stage('Git stage'){

            steps{

                checkout([$class: 'GitSCM', branches: [[name: '*/stage']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHub-Actions', url: 'https://github.com/hariharan-k21/Jenkins-Multistage-CICD.git']]])

            }
        }


        stage('Build image and Run image ') {

            steps{
                sh 'sudo su - jenkins -s /bin/bash'
                //sh 'sudo docker stop $imagename'
                //sh 'sudo docker rm $imagename'
                //sh 'sudo docker rmi $imagename'
                sh 'sudo docker image build -t  $imagename .'

            }

        }
        
        stage('Run image ') {

            steps{
                sh 'sudo docker run -p8000:5000 --restart=always --name $imagename  -itd $imagename'

            }

        }
        

        
    }
}
