pipeline {
    agent any
    
    stages {
        stage('Clean Workspace') {
            steps {
                script {
                    deleteDir()
                }
            }
        }
        
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build'){
             steps {
                script {
                    def javaSourcePath = 'src/Car.java'
                    bat 'mkdir lib'
                    bat "javac -d lib ${javaSourcePath}"
                }
            }
        }
    }

    post {
        always {
            junit 'src/reports/TEST-junit-jupiter.xml'
        }
        success {
            script {
                echo 'the build is success and the test genrated successfully'
                echo 'the webhook is working'
                emailext subject: 'Build Status',
                          body: 'Build was a success.',
                          to: 'mathanbabu.moorthi@expleogroup.com',
                          attachLog: true
            }
        }
        failure {
            script {
                emailext subject: 'Build Status',
                          body: 'Build was a failure',
                          to: 'mathanbabu.moorthi@expleogroup.com',
                          attachLog: true
            }
        }
    }
}
