pipeline {
  agent any
  
  stages {
    stage('docker-build') {
      steps {
        echo 'building docker image...'
        dir('kube-backend') {
          script {
            imgback = docker.build("inshiraa/jenkins-pipeline-backend")
          }
        }
      }
    }
    stage('docker-push') {
      steps {
        echo 'Push to dockerhub...'
        script {
          docker.withRegistry('', 'inshira-dockerhub-cred') {
            imgback.push()
          }
        }
      }
    }
  }
}
    stage('docker-deploy') {
        steps {
          echo 'Deploying to EC2...'
          sh'''
               sshpass -p hello123 ssh -o StrictHostKeyChecking=no ubuntu@18.117.148.201 "docker stop cicd-test && docker rm cicd-test && docker rmi inshiraa/jenkins-pipeline-backend:latest && docker run -d --name cicd-test -p 5000:5000 inshira/jenkins-backend:latest"
          '''
        }
    } 
  }
}
