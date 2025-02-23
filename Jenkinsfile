pipeline{
    agent any 

    tools{
        jdk 'jdk17'
        maven 'mvn3'
    }
    
    environment {
    SCANNER_HOME= tool 'sonarqube-scanner-jenkins'
    } 

    stages{
         
        stage('Git Checkout'){
            steps{
            git branch: 'main', url: 'https://github.com/MadhumithaRJ/jenkins_java_app.git'
            }
        }
        stage(' integration Test') {
            steps {
               sh "mvn clean install -DskipTests=true"
            }
        }

        stage('Maven Compile') {
            steps {
                sh "mvn compile"
            }

        }
        
        stage('SonarQube-Analysis') {
            steps {
                script {
                 echo "sonarqube code analysis"
                 withSonarQubeEnv(credentialsId: 'sonar-scanner') {
                     sh ''' $SCANNER_HOHE/bin/sonar-scanner -Dsonar.projectName=java-pipeline  -Dsonar.projectKey=java-pipeline \
                     -Dsonar.java.binaries=. '''
                     echo "End of sonarqube code analysis"

                   }
                }
            }
        }
    }
}