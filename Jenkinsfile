pipeline{
    agent any
    stages{
        stage('Checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/java']], extensions: [], userRemoteConfigs: [[credentialsId: 'pipe', url: 'https://github.com/MathanbabuMoorthi/java.git']])
            }
        }
        stage('Build'){
            steps{
                 script {
                    def javaSourceDir = 'src\\main\\java'

                    def classesDir = 'target\\class'
                    bat "mkdir ${classesDir}"

                    bat "javac -d ${classesDir} ${javaSourceDir}\\*.java"
                }
            }
        }
        
    }
}
