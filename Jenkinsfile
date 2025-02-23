pipeline{

    agent any
    environment {
    MAVEN_OPTS = "--add-opens jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED"
    } 

    stages{
         
        stage('Git Checkout'){
            steps{
            git branch: 'main', url: 'https://github.com/MadhumithaRJ/jenkins_java_app.git'
            }
        }
        stage('Unit Test maven'){
            steps{
               script{
                    sh 'mvn test'
               }
            }
        }
        stage('Integration Test maven'){
            steps{
               script{
                   sh 'mvn verify -DskipUnitTests'
               }
            }
        }
        stage('Static code analysis: Sonarqube'){
            steps{
               script{
                   withSonarQubeEnv('sonar-api') {
                   sh 'mvn clean package sonar:sonar -Dsonar.host.url=http://98.80.245.143:9000'
                   }
       
                }
            }
        }
    }
}