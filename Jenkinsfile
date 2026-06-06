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
        sh 'pytest tests.py'
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
  }
}
