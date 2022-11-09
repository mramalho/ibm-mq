pipeline { 
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    dockerapp = docker.build("mrsystem/ibm-mq:9.2.0.0-r2", '-f ./Dockerfile --no-cache .')
                }
            }
        }

        stage ('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        dockerapp.push('latest')
                    }
                }
            }
        }

        stage ('Deploy Kubernetes') {
            steps {
                withKubeConfig([credentialId: 'kubeconfig']) {
                    sh 'kubectl apply -f ./k8s/deployment.yaml -n mip-dev'
                }
            }
        }
    }
}
