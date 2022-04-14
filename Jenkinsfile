pipeline {
    agent any

    stages {
	stage('Test Code') {
	    steps {
		script{
                    if (fileExists("home/ubuntu/ming_docker/index.html")== true) {
                       echo 'File Exists'
                    } else {
                       echo 'File Not Exists'
                      // error('File not exists')
                    }
                }
	    }
        }
        stage('Build') {
            steps {
		script{
                echo 'Building..'
                app = docker.build("getintodevops/hellonode")
                }
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
