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
                    def javaSourcePath = 'src'
                    def targetPath = 'target\\class'
                    bat "mkdir ${targetPath}"
                    bat "javac -d ${targetPath} ${javaSourcePath}\\**\\*.java"
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
                emailext subject: 'Build Status',
                          body: 'Build was a success.',
                          to: 'mr.mathan5555@gmail.com',
                          attachLog: true
            }
        }
        failure {
            script {
                emailext subject: 'Build Status',
                          body: 'Build was a failure',
                          to: 'mr.mathan5555@gmail.com',
                          attachLog: true
            }
        }
    }
}
