pipeline {
    agent any

    stages {
        stage('docker-build') {
            steps {
                echo 'building docker image...'
                dir('kube-backend') {
                    script {
                        imgback = docker.build("jenkins-pipeline-backend")
                    }    
                }
            }
        }    
        stage('docker-push') {
            steps {
                echo 'Push to dockerhub...'
                script {
                    docker.withRegistry(", 'inshira-dockerhub-cred') {
                        imgback.push()
                    }
                }                       
            }
        }
        stage('deploy') {
            steps {
                echo 'Deploying the project in EC2...'
            }
        }    
    }
}
