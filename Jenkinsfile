pipeline {
    agent any
    environment {
        registryCredential = 'dockerhub'
        }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t danialkhan1221/test-node-app .'
            }   
        }
        stage('Test') {
            steps {
                sh 'docker container rm -f node'
                sh 'docker container run -p 8001:8080 --name node -d danialkhan1221/test-node-app'
            }
        }
        stage('Publish') {
            steps{
                script {
                    docker.withRegistry( '', registryCredential ) {
                        sh 'docker push danialkhan1221/test-node-app:latest'
                    }
                }
            }
        }
    }
}
