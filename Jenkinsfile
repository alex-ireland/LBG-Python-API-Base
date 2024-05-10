pipeline {
    agent any
    environment {
    runDeployment = false
    CONTAINER_NAME = "lbg-web-app"
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
	        //withPythonEnv("python3") {
                //    sh "python3 lbg.test.py"
                //}

                sh "echo testing..."
                sh "docker exec '${CONTAINER_NAME}' python lbg.test.py"
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
