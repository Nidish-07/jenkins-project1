pipeline {
    agent any
    tools {
        maven 'Maven 3.5.0'
    }
    stages {
        stage('Build Maven') {
            steps {
                script {
                    // Correct checkout step
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Nidish-07/jenkins-project1.git']])
                    // Correct Maven build command for Unix-based systems
                    sh 'mvn clean install'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Make sure Docker is installed and available in the PATH
                    sh 'docker build -t nidish07/project1 .'
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    // Use credentials to log in to Docker Hub
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                        sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                        sh "docker push nidish07/project1"
                    }
                }
            }
        }
    }
}
