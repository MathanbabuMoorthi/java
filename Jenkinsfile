pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                 script {
                    def javaSourceDir = 'src\\main\\java'

                    def classesDir = 'target\\class'
                    bat "mkdir ${classesDir}"
                    bat "javac -d ${classesDir} ${javaSourceDir}\\App.java ${javaSourceDir}\\Car.java ${javaSourceDir}\\CarTest.java"

                }
            }
        }
        
    }
}
