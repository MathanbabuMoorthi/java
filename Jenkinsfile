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
        stage('Build'){
            steps{
                 script {
                    def javaSourceDir = 'src'
                    def classesDir = 'target\\files'
                    bat "mkdir ${classesDir}"
                    bat "javac -d ${classesDir} ${javaSourceDir}\\App.java ${javaSourceDir}\\Car.java ${javaSourceDir}\\CarTest.java"

                }
            }
        }
    }
}
