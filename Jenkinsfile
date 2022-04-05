// Jenkinsfile (Declarative Pipeline)
DOCKER_IMAGE = 'hub.docker.com/_/nginx'
pipeline {
    agent {
        docker { image 'alipne:latest' }
    }
    options { 
          skipDefaultCheckout()
          disableConcurrentBuilds()
          parallelsAlwaysFailFast()
    }
    stages {
        stage('Test Docker'){
            steps{
                sh 'ls -l'
            }
        }
        stage('Build') {
            steps {
                sh '''
                cat /etc/os-release
                echo Building
                '''

                sh '''
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
