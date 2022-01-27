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
            agent {
                docker{
                image DOCKER_IMAGE
                alwaysPull true
                }
            }

            steps {
                sh 'ls -la'
                echo 'Building..'
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
