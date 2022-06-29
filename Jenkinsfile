pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '20'))
        disableConcurrentBuilds()
    }

    triggers {
        cron('H H(9-18)/4 * * 1-5')
        pollSCM('H/5 * * * *')
    }

    agent {
        docker {
            image 'node:8.9-alpine'
            // args '-v /var/lib/jenkins/.m2:/home/obe-developer/.m2'
        }
    }

    stages {

        stage('Clone repo') {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: 'refs/heads/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/nicopaez/passwordapi.git']]])
            }
        }

        stage('Solve dependencies') {
            stage('Frontend') {
                steps {
                    sh "npm install"
                }
            }
        }


    post {
        failure {
            mail(to: "equipo@xxxxx.com.ar",
                 subject: "Falló en #${BUILD_NUMBER}",
                 body: "body",
                 from: "Jenkins",
                 mimeType: "text/html"
            )
        }

        fixed {
            mail(to: "equipo@xxxx.com.ar",
                 subject: "Se arregló en #${BUILD_NUMBER}",
                 body: "Body",
                 from: "Jenkins",
                 mimeType: "text/html"
            )
        }

        always {
            sh 'echo "the END"'
        }
    }
}
