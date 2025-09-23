pipeline {
    agent any

    environment {
        IMAGE_NAME = "docker.io/sharuk19/docker:latest"
        GIT_REPO = "https://github.com/Sharuk19/docker-jenkins-github-cicd.git"   // replace with your repo
    }

    stages {
        stage('Checkout from GitHub') {
            steps {
                git branch: 'main', url: "${GIT_REPO}"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat """
                        docker build -t %IMAGE_NAME% .
                    """
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    bat """
                        echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin
                        docker push %IMAGE_NAME%
                    """
                }
            }
        }
        stage("Create a Container") {
            steps{
                bat 'docker run -d -p8081:80 --name myapp sharuk19/docker:latest'
            }
        }
    }


    triggers {
        pollSCM('H/5 * * * *')   // Poll GitHub every 5 minutes for changes
    }
}
