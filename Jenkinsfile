pipeline {
    agent any

    stages {
        stage('source') {
        steps {
          echo 'cloning from github...'
          sh'''
          git clone --branch main --single-branch 'https://github.com/inshiraa/two-tier-demo.git' 
          '''
        }
      } 
        stage('pre-build') {
        steps {
          echo 'this is the pre-build stage...'
        }
      } 
        stage('build') {
            steps {
                echo 'building docker image'
            }
        }
        stage('test') {
            steps {
                echo 'Testing the project'
            }
        }
        stage('deploy') {
            steps {
                echo 'Deploying the project in EC2'
            }
        }    
    }
}
