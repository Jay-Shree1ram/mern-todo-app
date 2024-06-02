pipeline {
    agent any
    
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials-id')
        FRONTEND_IMAGE = 'spygram/frontend-image'
        BACKEND_IMAGE = 'spygram/backend-image'
        FRONTEND_TAG = 'latest'
        BACKEND_TAG = 'latest'
    }
    
    stages {
        stage("SCM") {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Spygram/mern-todo-app.git']])
            }
        }
        
        stage("build docker image"){
            steps{
                sh "docker compose up -d --build"
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}	
