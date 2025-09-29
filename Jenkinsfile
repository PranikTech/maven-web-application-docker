pipeline{

    agent any 

    tools
    {
        maven 'Maven_3.9.7'
    }

    environment
    {
        buildNumber = "${BUILD_NUMBER}"
    }

    stages 
    {
        stage('Git Checkout')
        {
            steps()
            {
                git branch: 'docker_cicd', url:'https://github.com/PranikTech/maven-web-application-docker.git'
            }
        }
        stage('Build Project Artifact using Maven ')
        {
            steps()
            {
                sh 'mvn clean package'
            }
        }
        stage('Build Docker Image')
        {
            steps()
            {
                sh 'docker build -t sourabh054/dockercicd:${buildNumber} .'
            }
        }
        stage('Push Docker Image to DockerHub Registry')
        {
            steps()
            {
                withCredentials([string(credentialsId: 'Docker_Hub_Password', variable: 'Docker_Hub_Password')]) 
                {
                  sh 'docker login -u mithuntechnologies -p ${Docker_Hub_Password}'
                 }
                sh 'docker push sourabh054/dockercicd:${buildNumber}'
            }
        }
    }
}