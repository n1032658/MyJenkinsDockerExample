pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred')
	}

	stages {
	
	stage('Continuous Download') 
   
	 {
	 steps {
  checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '7d0c66bf-4a63-4385-b6b0-af1d614e247c', url: 'https://github.com/n1032658/MyJenkinsDockerExample.git']]])
 
	 }}
	
stage("build") {
  steps {
      sh 'docker build -t  mynginx  .'
  }
    }
	stage("remove containers ") {
		  steps {
   sh 'docker rm -f $(docker ps -a -q)'
		  }
    }
	 stage("run") {
		  steps {
   sh 'docker run --name mynginxcontainer -d -p 80:80 mynginx'
		  }
    }
		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push mdasari8019/dummyapp:latest'
			}
		}
	}



}
