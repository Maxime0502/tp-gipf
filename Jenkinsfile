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
                sh './gradlew -Dhttps.proxyHost=proxy1-rech.uphf.fr -Dhttps.proxyPort=3128 - -Dsonar.token=sqp_b8ef7905b703b9726b441acba9a1e126f2d40e97'
            }
        }
        stage('Jar'){
            steps{
                sh './gradlew -Dhttps.proxyHost=proxy1-rech.uphf.fr -Dhttps.proxyPort=3128 jar'
            }
        }
        
            
    }
}
