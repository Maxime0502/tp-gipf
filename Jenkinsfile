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
        stage('SonarQube'){
            steps{
                withSonarQubeEnv('sonar') {
                    sh "./gradlew -Dhttps.proxyHost=proxy1-rech.uphf.fr -Dhttps.proxyPort=3128 sonar -Dsonar.projectName='Projet 1' -Dsonar.host.url=http://172.17.0.1:9000 -Dsonar.token=sqp_b8ef7905b703b9726b441acba9a1e126f2d40e97"
                }
            }
        }
        
            
    }
}
