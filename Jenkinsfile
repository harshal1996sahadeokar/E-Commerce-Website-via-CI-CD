pipeline {
    agent any

    stages {
        stage('Change sudo') {
            steps {
                script {
                    // Running a command with sudo
                    sh "sudo whoami"
                }
            }
        }
        
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t harshalsahadeokar/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push harshalsahadeokar/adservice:latest"
                    }
                }
            }
        }
    }
}
