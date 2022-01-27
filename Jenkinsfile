// Jenkinsfile (Declarative Pipeline)
pipeline {
      agent any
      options { 
          skipDefaultCheckout()
          disableConcurrentBuilds()
          parallelsAlwaysFailFast()
       }
    stages {
        stage('Build') {
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
