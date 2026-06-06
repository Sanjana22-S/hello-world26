pipeline {
  agent any
  stages {
    stage('git repo') {
      steps {
        git 'https://github.com/Sanjana22-S/hello-world26.git'
      }
    }
    stage('Dependencies') {
      steps {
        sh 'python3 -m pip install -r requirements.txt'
      }
    }
    stage('Test') {
      steps {
        sh 'pytest test.py'
      }
    }
    stage('Build') {
      steps {
        sh 'tar -czf hello-world.tar.gz *'
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts artifacts: 'hello-world.tar.gz', fingerprint: true
      }
    }
	stage('Deploy') {
		steps {
			sh '''
			scp -i mypem-key.pem hello-world.tar.gz ec2-user@43.204.22.121:/home/ec2-user/
			ssh -i mypem-key.pem ec2-user@43.204.22.121 "tar -xzf hello-world.tar.gz && nohup python3 app.py &"
			'''
		}
	}

  }
}
