node('master'){
 
 stage('Continuous Download') 
   
	 {
	
  checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '7d0c66bf-4a63-4385-b6b0-af1d614e247c', url: 'https://github.com/n1032658/MyJenkinsDockerExample.git']]])	}
	
    stage("build") {
 
      sh 'docker build -t  mynginx  .'
      
    }
    stage("run") {
   sh 'docker run --name mynginxcontainer -d -p 80:80 mynginx'
    
    }
  
}