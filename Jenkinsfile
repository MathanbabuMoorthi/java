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
                    bat "javac -d target\\class ${javaSourceFile}"
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
