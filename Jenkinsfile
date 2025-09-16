pipeline {
    agent any

    environment {
        IMAGE_NAME = "sharukahamed/myportfolio:latest"
        GIT_REPO = "https://github.com/Sharuk19/DevOpsProjects.git"  // replace with your repo
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
                    // Dockerfile is inside myapp folder
                    bat """
                        docker build -t %IMAGE_NAME% -f myapp/Dockerfile myapp
                    """
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    bat """
                        echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin
                        docker push %IMAGE_NAME%
                    """
                }
            }
        }
    }

    triggers {
        pollSCM('H/5 * * * *') // Poll GitHub every 5 minutes for changes
    }
}
