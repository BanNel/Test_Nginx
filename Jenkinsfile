pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                script{

                echo 'Testing..'
                final String url = "http:localhost:8080"
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
