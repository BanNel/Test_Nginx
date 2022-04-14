pipeline {
    agent any

    stages {
	stage('Test Code') {
	    when { not{ expression { return fileExists ('/home/ubuntu/ming_docker/index.html') } } }
	    steps {
        	   echo "file not exists"
                   error("Test failed: file not exists")
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
