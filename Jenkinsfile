pipeline{
    agent any
    stages{
        stage('Clean Workspace') {
            steps {
                script {
                    deleteDir()
                }
            }
        }
        stage('Checkout'){
            steps{
                checkout scm
                }
        }
        post{
            always{
                junit 'TEST-junit-jupiter.xml'
            }
            success{
                emailtext(
                    subject: 'Build Status',
                    body: 'Build was a success.',
                    to: 'mr.mathan5555@gmail.com',
                    attachlog: true
                )
            }
            failure{
                emailtext(
                    subject: 'Build Status',
                    body:'Build was a failure',
                    to: 'mr.mathan5555@gmail.com',
                    attachlog: true
                )
            }
        }
        
        
    }
}
