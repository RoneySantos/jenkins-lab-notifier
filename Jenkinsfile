// Jenkinsfile (Declarative Pipeline)
pipeline {
      agent any
//       options { skipDefaultCheckout() }
      
    stages {
        stage('Build') {
            steps {
                sh 'ls -la'
                echo 'Building..'
//                 slackSend (color: 'good', message: "Building - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')  
            }
        }
        stage('Test') {
            steps {
                sh 'ls -la'
//                 slackSend (color: 'good', message: "Testing - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')
                           
            }
        }
        stage('Deploy') {
            steps {
                sh 'ls -la'
                echo 'Deploying....'
//                 slackSend (color: 'good', message: "Deploying - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')  
            }
        }
    }

}
