# DevOpsProjects
# DevOps Project - Jenkins CI/CD with Docker  

This project demonstrates how to build, test, and push a Docker image to **Docker Hub** using a **Jenkins Pipeline (Jenkinsfile)**.  

---

## Project Overview  
- Source code and Dockerfile are stored in GitHub.  
- Jenkins automatically pulls the latest code from GitHub.  
- Jenkins builds the Docker image from the Dockerfile.  
- The image is tagged and pushed to **Docker Hub**.  

---

## Tech Stack  
- Jenkins – CI/CD automation  
- Docker – Image build & containerization  
- GitHub – Source Code Management  
- Docker Hub – Container Registry  

---

## Project Structure  
DevOpsProjects/
project1/
   Dockerfile
   index.html
   Jenkinsfile

## Pre-Requisites

Jenkins installed with Pipeline and Docker Pipeline plugins
Docker installed on Jenkins server
Docker Hub account & repository created
Jenkins credential ID: dockerhub-credentials
