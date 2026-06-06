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

    stage('Deploy') {
      steps {
        sh '''
          pkill -f app.py || true
          nohup python3 app.py > app.log 2>&1 &
        '''
      }
    }
  }

  post {
    success {
      echo 'Build and deployment completed successfully!'
    }
    failure {
      echo 'Pipeline failed!'
    }
  }
}
