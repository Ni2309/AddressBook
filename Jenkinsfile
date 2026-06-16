pipeline {
    agent any

    stages{
        stage('Checkout') {
            step{
		checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Ni2309/AddressBook.git']])
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
