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
                sh "./gradlew sonar -Dsonar.projectKey=Projet-1 -Dsonar.projectName='Projet 1' -Dsonar.host.url=http://172.17.0.1:9000 -Dsonar.token=sqp_0002714bfc86c838247a17a34678111f907ed2a0 jacocoTestCoverageVerification"
            }
        }
        stage('Jar'){
            steps{
                sh './gradlew -Dhttps.proxyHost=proxy1-rech.uphf.fr -Dhttps.proxyPort=3128 jar'
            }
        }
        
            
    }
}
