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
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                    dockerapp.push('latest')
                }
            }
        }
    }
}