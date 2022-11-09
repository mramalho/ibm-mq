pipeline { 
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    dockerapp = docker.build("ibmcom/mq:9.2.0.0-r2", '-f ./Dockerfile .')
                }
            }
        }

        stage ('Push Image') {
            steps {
                script {
                    docker.withDockerRegistry(url: 'https://registry.hub.docker.com', credentialsId: 'dockerhub')
                    dockerapp.push('latest')
                }
            }
        }
    }
}
