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
        // stage('Test Docker'){
        //     steps{
        //         sh 'node --version'
        //     }
        // }
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
        stage('FTP Test 1'){
            agent{
                docker { image 'nginx:latest' }
            }
            steps{
                sh 'cat /etc/os-release'
            }
        }
        stage('FTP Test 2'){
            agent{
                docker { image 'alpine:latest' }
            }
            steps{
                sh 'cat /etc/os-release'
            }
        }
        // stage('Artefatos'){
        //     steps{
        //         archiveArtifacts artifacts: 'build/'
        //     }
        // }
    }
    post{
        always {
            // sh(script: "ACTUAL_HOUR=\$(date '+%F-%H-%M-%S')", returnStatus: false, returnStdout: true)
            // sh(script: "echo ${currentBuild.durationString} > ${env.WORKSPACE}/build_duration_\$ACTUAL_HOUR.txt", returnStatus: false, returnStdout: true)
            sh(script: "echo ${currentBuild.durationString} > ${env.WORKSPACE}/build_duration.txt", returnStatus: false, returnStdout: true)
            archiveArtifacts artifacts: 'build_duration.txt', allowEmptyArchive: true
        }
    }
}
