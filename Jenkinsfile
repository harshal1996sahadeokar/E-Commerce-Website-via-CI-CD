pipeline {
    agent any
  stages {
        stage('Change sudo') {
            steps {
                script {
                     {
                        sh "sudo su"
                    }
                }
            }
        }
    stages {
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
                        sh "docker push harshalsahadeokar/adservice:latest "
                    }
                }
            }
        }
    }
}
