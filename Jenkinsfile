pipeline {
    agent any

    stages {
	stage('Test Code') {
	    when { expression { return fileExists ('/home/ubuntu/ming_docker/index.html') } }
	    steps {
        	   echo "file exists"
	          }
	    }

        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                script{

                echo 'Testing..'
                final String url = "http://localhost:8080"
                final String response = sh(script: "curl -s $url", returnStdout: true).trim()

                echo response

                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
