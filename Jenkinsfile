pipeline {
    agent  { label 'slave1'}
    stages {
        stage(clone) {
            steps {
                sh 'cd /home/slave1/'
                sh 'git clone https://github.com/Manjunathhm/java-mvn-hello-world-web-app.git'
                sh 'pwd'
                sh 'cd /home/slave1/workspace/ProjectOne'
            }
        }
        stage(buildImage) {
  		steps {
                	sh 'cd /home/slave1/workspace/ProjectOne'
                  	sh 'sudo docker build -t mavenbuild /home/slave1/workspace/ProjectOne'
			sh 'sudo docker tag mavenbuild:latest 155635587501.dkr.ecr.us-east-2.amazonaws.com/private_repo1:latest'
                        sh 'sudo docker push 155635587501.dkr.ecr.us-east-2.amazonaws.com/private_repo1:latest'
            	}
	}
         stage(runApp) {
           steps {
                    sh 'cd /home/slave1/workspace/ProjectOne'
                    sh 'sudo docker run -d -p 8090:8080 mavenbuild:latest'
		}
	   }
	}
}
