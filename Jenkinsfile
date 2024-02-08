pipeline {
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    dockerapp = docker.build("davescott99/astroflix-discovery-service:${env.BUILD_ID}", "-f ./discovery/Dockerfile ./discovery")
                }
            }
        }

        stage ('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }


    }
}