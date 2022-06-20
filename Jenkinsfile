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
        // stage('FTP Test 3'){
        //     agent{
        //         docker { image 'nginx:latest' }
        //     }
        //     steps{
        //         sh '''
        //         su - root
        //         cat /etc/os-release
        //         apt-get install ftp -y
        //         cd $HOME
        //         touch test-$(date +%F-%H-%M-%S).txt
        //         # script to send FTP
        //         HOST='dockerfile_ftp_1'
        //         USER='ekode'
        //         PASSWD='ekode123'
        //         FILE='test*'

        //         ftp -n $HOST <<END_SCRIPT
        //         quote USER $USER
        //         quote PASS $PASSWD
        //         binary
        //         put $FILE
        //         quit
        //         END_SCRIPT
        //         exit 0
        //         '''
        //     }
        // }
        // stage('FTP Test 3') {
        //     steps {
        //         script {
        //             docker.image('nginx:latest').inside("""
        //             -u 0:0
        //             --network=dockerfile_default
        //             """) {
        //         sh '''
        //         su - root
        //         cat /etc/os-release
        //         apt-get update
        //         apt-get install ftp -y
        //         cd $HOME
        //         touch test-$(date +%F-%H-%M-%S).txt
        //         # script to send FTP
        //         HOST='dockerfile_ftp_1'
        //         USER='ekode'
        //         PASSWD='ekode123'
        //         FILE='test*'

        //         ftp -n $HOST <<END_SCRIPT
        //         quote USER $USER
        //         quote PASS $PASSWD
        //         binary
        //         put $FILE
        //         quit
        //         END_SCRIPT
        //         exit 0
        //         '''
        //             }
        //         }
        //     }
        // }
    //     stage('FTP Test 4') {
    //         steps {
    //             script {
    //             sh '''
    //             cd $HOME
    //             touch test-$(date +%F-%H-%M-%S).txt
    //             # script to send FTP
    //             HOST='dockerfile_ftp_1'
    //             USER='ekode'
    //             PASSWD='ekode123'
    //             FILE='test*'

    //             ftp -n $HOST <<END_SCRIPT
    //             quote USER $USER
    //             quote PASS $PASSWD
    //             binary
    //             put $FILE
    //             quit
    //             END_SCRIPT
    //             exit 0
    //             '''
    //             }
    //         }
    //     }
    // }
    }
    post{
        always {
            // test using
            // // sh(script: "ACTUAL_HOUR=\$(date '+%F-%H-%M-%S')", returnStatus: false, returnStdout: true)
            // // sh(script: "echo ${currentBuild.durationString} > ${env.WORKSPACE}/build_duration_\$ACTUAL_HOUR.txt", returnStatus: false, returnStdout: true)
            // sh(script: "echo ${currentBuild.durationString} > ${env.WORKSPACE}/build_duration.txt", returnStatus: false, returnStdout: true)
            // archiveArtifacts artifacts: 'build_duration.txt', allowEmptyArchive: true
            // // incluido para teste
            // script {
            // docker.image('alpine:latest').inside("""
            //         -u 0:0
            //         --network=dockerfile_default
            //         """) {
            //     sh '''
            //     apk add lftp
            //     cd $HOME
            //     touch test-$(date +%F-%H-%M-%S).txt
            //     HOST='dockerfile_ftp_1'
            //     USER='ekode'
            //     PASSWD='ekode123'
            //     FILE='test*'
            //     lftp -u $USER,$PASSWD $HOST <<END_SCRIPT
            //     mput *
            //     bye
            //     END_SCRIPT
            //     exit 0
            //     '''
            def notifySlack(String buildStatus = 'STARTED') {
            // Build status of null means success.
            buildStatus = buildStatus ?: 'SUCCESS'

            def color

            if (buildStatus == 'STARTED') {
                color = '#D4DADF'
            } else if (buildStatus == 'SUCCESS') {
                color = '#BDFFC3'
            } else if (buildStatus == 'UNSTABLE') {
                color = '#FFFE89'
            } else {
                color = '#FF9FA1'
            }

            def msg = "${buildStatus}: `${env.JOB_NAME}` #${env.BUILD_NUMBER}:\n${env.BUILD_URL}"

            slackSend(color: color, message: msg)
            }
            
            try {
                notifySlack()

                // Existing build steps.
            } catch (e) {
                currentBuild.result = 'FAILURE'
                throw e
            } finally {
                notifySlack(currentBuild.result)
            }
        }
    }
}
