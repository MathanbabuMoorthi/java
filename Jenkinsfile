pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    def javaSourceDir = 'src/main/java'
                    def classesDir = 'target/classes'
                    
                    bat "mkdir ${classesDir}"
                    bat "javac -d ${classesDir} ${javaSourceDir}/App.java ${javaSourceDir}/Car.java ${javaSourceDir}/CarTest.java"
                }
            }
        }
    }
}
