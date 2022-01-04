// Jenkinsfile (Declarative Pipeline)
pipeline {
      agent any  
//    agent {
//        docker { image 'node:14-alpine' }
    stages {
        stage('Build') {
            steps {
                sh 'mkdir lab-teste-jenkins'
                echo 'Building..'
                slackSend (color: 'good', message: "Building - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')  
            }
        }
        stage('Test') {
            steps {
                sh 'ls -la'
                slackSend (color: 'good', message: "Testing - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')
                           
            }
        }
        stage('Deploy') {
            steps {
                sh 'rm -rf lab-teste-jenkins'
                echo 'Deploying....'
                slackSend (color: 'good', message: "Deploying - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')  
            }
        }
        stage('Notificando o usuario') {
            steps {
//                slackSend "Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
                slackSend (color: 'good', message: "Finish - ${env.JOB_NAME} ${env.BUILD_NUMBER} ${env.CHANGE_AUTHOR} ${env.CHANGE_AUTHOR_DISPLAY_NAME} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')  
//                slackSend (failOnError: true, message: "Build Failed - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'testelabjenkins')
//              slackSend (color: 'good', message: '[ Sucesso ] O novo build esta disponivel em: http://192.168.33.10:81/ ', tokenCredentialId: 'testelabjenkins')
            }
        }
    }
    post { // write in the log file
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
            slackSend (color: 'good', message: "The pipeline ${currentBuild.fullDisplayName} completed successfully.", tokenCredentialId: 'testelabjenkins') //if passed send menssage in the slack
        }
        unstable {
            echo 'I am unstable :/' //write message in the log file
        }
        failure {
            echo 'I failed :('
            slackSend (color: 'danger', message: "The pipeline ${currentBuild.fullDisplayName}  failed.", tokenCredentialId: 'testelabjenkins') // if fail send message in the slack
        }
        changed {
            echo 'Things were different before...'  //write message in the log file
        }
    }
}
