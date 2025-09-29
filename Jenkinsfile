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
    }
}