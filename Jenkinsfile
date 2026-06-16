pipeline {
    agent any

    tools {
        maven 'Maven3'   // Must match Jenkins Tools name exactly
    }

    stages {

        stage('Prepare Workspace') {
            steps {
                echo 'Cleaning workspace to avoid old target issues'
                cleanWs()
            }
        }

        stage('Checkout') {
            steps {
                echo 'Cloning source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building project using Maven'
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                sh 'mvn test'
            }
        }

        stage('Check Artifact') {
            steps {
                echo 'Checking target folder content'
                sh 'ls -la target || true'
                sh 'find target -name "*.jar" || true'
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving JAR file'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage (add EC2/Docker deploy here)'
            }
        }

    }

    post {
        always {
            echo 'Pipeline finished'
        }
        success {
            echo 'Build SUCCESS'
        }
        failure {
            echo 'Build FAILED'
        }
    }
}
