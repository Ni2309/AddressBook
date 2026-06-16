pipeline {
    agnent any
    tools {
        maven 'Maven3'
    }

    stages {
        stage('CheckOut'){
            steps {
                echo 'Checking out the code from GitHub'
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Ni2309/AddressBook.git']])
            }
        }
        
        stage('Install') {
            steps {
                echo 'Installing dependencies using Maven'
                sh 'mvn clean'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project using Maven'
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests using Maven'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the project using Maven'
                sh 'mvn package'
            }
        }
        
        stage('Archive') {
            steps {
                echo 'Archiving the built artifact'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }
}
