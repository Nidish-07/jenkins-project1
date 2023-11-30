# devops-automation
# Jenkins Project with Maven and Docker

This project is a demonstration of a Jenkins pipeline that automates the build and deployment process for a Java project using Maven and Docker. The pipeline is designed to run on an AWS Ubuntu instance, showcasing a typical setup for continuous integration and continuous delivery (CI/CD) workflows.

## Project Overview

The goal of this project is to showcase how Jenkins can be used to streamline the software development lifecycle by automating the following key steps:

1. **Build Maven Project:** The pipeline fetches the source code from a Git repository and uses Maven to build the Java project. This ensures that the application is compiled and dependencies are resolved.

2. **Build Docker Image:** After a successful Maven build, the pipeline creates a Docker image containing the application. This step encapsulates the application and its dependencies into a portable container.

3. **Push to Docker Hub:** The Docker image is then pushed to Docker Hub, a cloud-based registry for Docker images. This makes the application easily accessible and deployable from any environment with Docker support.

## Prerequisites

Before running the Jenkins pipeline, make sure the following tools are installed on your system:

- [Jenkins](https://www.jenkins.io/doc/book/installing/)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Maven](https://maven.apache.org/install.html)
- [Docker](https://docs.docker.com/get-docker/)

## Setup Instructions

### 1. Install Jenkins on AWS Ubuntu

Follow the [official Jenkins installation guide for Ubuntu](https://www.jenkins.io/doc/book/installing/#debian-ubuntu).

### 2. Install Git, Maven, and Docker on AWS Ubuntu

Run the following commands on your AWS Ubuntu instance:

```bash
sudo apt-get update
sudo apt-get install git
sudo apt-get install maven
sudo apt-get install docker.io
sudo systemctl start docker
sudo systemctl enable docker

3. Jenkins Configuration
Add Docker Hub credentials in Jenkins: Go to "Manage Jenkins" -> "Manage Credentials" -> "(global)" and add Docker Hub username and password.

Ensure Jenkins user has Docker permissions: Run the following commands:

bash
Copy code
sudo usermod -aG docker $USER
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
4. Run Jenkins Pipeline
Create a new pipeline project in Jenkins, configure it to use the Git repository, and set up the pipeline script from Jenkinsfile.

5. Trigger the Pipeline
Run the pipeline manually or configure a webhook to trigger it automatically on code changes.

Additional Tips
Customize the Maven tool version and other configurations in the Jenkinsfile.
Adjust Docker image names and tags in the Docker build and push steps.
Feel free to adapt this README based on your project's specific details. Happy coding!
