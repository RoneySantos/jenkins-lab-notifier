// Jenkinsfile (Declarative Pipeline)
pipeline {
      agent any
      options { 
          skipDefaultCheckout()
          disableConcurrentBuilds()
          parallelsAlwaysFailFast()
       }
      
    stages {

        // stage('Paralelizando') {
        // parallel {
        stage('Build') {
            steps {
                sh 'ls -la'
                echo 'Building..'
                //def userId=slackUserIdFromEmail('jonissonfn@gmail.com')
                //slackSend(color: "good", message: "<@$userId> Message from Jenkins Pipeline")
                //slackSend (color: "good", message: "<jonissonfn@gmail.com> Essa mensagem vai somente para o Jonisson")
                // slackSend (color: 'good', message: "Building - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')
                sleep 30  
            }
        }
        stage('Test') {
            steps {
                sh 'ls -la'
//                 slackSend (color: 'good', message: "Testing - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')
                // sleep 30
                           
            }
        }
        stage('Deploy') {
            steps {
                sh 'ls -la'
                echo 'Deploying....'
                // sleep 30
//                 slackSend (color: 'good', message: "Deploying - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')  
            }
        }
    }
    //     }
    // }

}
