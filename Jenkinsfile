pipeline{
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages{
        stage('Build Docker Image'){
            
            sh "docker build -t taj/dockerwebapp:${DOCKER_TAG}"
        }
    }
}

def getDockerTag(){
    def tag = sh script: 'git rev-parse HEAD', retirnStdout: true 
    return tag
}