pipeline {
    agent any
    environment {
    runDeployment = false
    }
    stages {
        stage('Build') {
            steps {
		sh "echo building..."
                sh "sh setup.sh"
           }
        }
	stage('Test') {
            steps {
	        withPythonEnv("python3") {
                    sh "python lbg.test.py"
                }
            }
	}
        stage('Deploy') {
            when { expression { runDeployment } }
            steps {
                sh "echo deploying..."
            }
        }
    }
}
