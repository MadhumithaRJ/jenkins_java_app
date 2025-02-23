pipeline{

    agent any

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
       
    }
}