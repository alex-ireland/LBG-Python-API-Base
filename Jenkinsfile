pipeline {
    agent any
    environment {
    runDeployment = false
    }
    stages {
        stage('Build') {
            steps {
                sh "sh setup.sh"
           }
        }
        stage('Deploy') {
            when { expression { runDeployment = true } }
            steps {
                sh "echo deploying"
            }
        }
    }
}
