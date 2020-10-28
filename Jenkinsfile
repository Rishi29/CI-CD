pipeline{
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages{
        stage('Build Docker Image'){
            steps{
                sh "sudo docker build . -t taj/dockerwebapp:${DOCKER_TAG}"
            }
        }
        stage('DockerHub Push'){
                steps{
                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
                sh "sudo docker login -u rishi29 -p ${dockerHubPwd}"
                sh "sudo docker push taj/dockerwebapp:${DOCKER_TAG}"
                }
}
        }
    }
}

def getDockerTag(){
    def tag = sh script: 'git rev-parse HEAD', returnStdout: true 
    return tag
}