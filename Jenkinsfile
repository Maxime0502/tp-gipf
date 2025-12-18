pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Compilation') {
            steps {
                sh './gradlew -Dhttps.proxyHost=proxy1-rech.uphf.fr -Dhttps.proxyPort=3128 compileJava'
            }
        }
        stage('Test'){
            steps{
                sh './gradlew -Dhttps.proxyHost=proxy1-rech.uphf.fr -Dhttps.proxyPort=3128 test'
        }
        }
        stage('SonarQube'){
            steps{
                withSonarQubeEnv() {
                    sh './gradlew -Dsonar.projectName='Projet 1' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_b8ef7905b703b9726b441acba9a1e126f2d40e97'
                }
            }
        }
        
            
    }
}
