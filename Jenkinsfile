pipeline {
  agent {
    docker { image 'python:3.10' }
  }
  stages {
    stage('Checkout') {
      steps { git 'https://github.com/Sanjana22-S/hello-world26.git' }
    }
    stage('Dependencies') {
      steps { sh 'pip install -r requirements.txt' }
    }
    stage('Test') {
      steps { sh 'pytest test.py' }
    }
    stage('Build') {
      steps { sh 'tar -czf hello-world.tar.gz *' }
    }
    stage('Archive') {
      steps { archiveArtifacts artifacts: 'hello-world.tar.gz', fingerprint: true }
    }
  }
}
