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
	    withPythonEnv("python3") {
                sh "python lbg.test.py"
            }
	}
        stage('Deploy') {
            when { expression { runDeployment = true } }
            steps {
                sh "echo deploying..."
            }
        }
    }
}
