pipeline {
    agent any

    stages{
        stage('Checkout') {
            step{
                echo ("Checking out source code from GitHub")
            }
        }
        stage('Build') {
            step{
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            step{
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            step{
                echo 'Deploying application to production environment'
            }
        }           
    }
}
