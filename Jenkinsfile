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
		steps{
	            sshagent(credentials : ['Barry_ec2_Key']) {
	            sh """ssh -tt ubuntu@3.141.45.246 << EOF 
                    git --version
                    sudo docker ps
                    sudo docker system prune -f
                    cd /home/ubuntu/ming_docker
                    sudo docker build -t ihaveanicecream/nginx-custom-index .
                    sudo docker push ihaveanicecream/nginx-custom-index
                    aws ecs update-service --cluster  Barry-Nginx --service Nginx --force-new-deployment
                    
                    exit
                    EOF"""
          
            }
        }
        }
    }
}
