pipeline { 
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    dockerapp = docker.build("ibmcom/mq:9.2.0.0-r2", '-f ./Dockerfile --no-cache .')
                }
            }
        }

        stage ('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub'){
                    }
                }
               
            }
        }

        stage ('Deploy Kubernetes') {
            steps {
                withKubeConfig([credentialId: 'kubeconfig'])
                   sh 'kubectl apply -f '
                }
               
            }
        }

    }
}
