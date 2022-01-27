// Jenkinsfile (Declarative Pipeline)
DOCKER_IMAGE = 'hub.docker.com/_/nginx'
pipeline {
      agent any
      options { 
          skipDefaultCheckout()
          disableConcurrentBuilds()
          parallelsAlwaysFailFast()
       }
    stages {
        stage('Build') {
            // agent {
            //     docker {
            //     image 'node:16.13.1-alpine'
            //     alwaysPull true
            //     }
            // }
            steps {
                sh '''
                cat /etc/os-release
                echo Building
                '''

                '''
                echo Segunda parte do step Build
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'ls -la'             
            }
        }
        stage('Deploy') {
            steps {
                sh 'ls -la'
                echo 'Deploying....'
            }
        }
    }
}
