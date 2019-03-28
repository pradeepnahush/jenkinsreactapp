pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
        echo 'NPM Packages has been loaded..'
      }
    }
    stage('Test') {
      steps {
        sh 'bash ./jenkins/scripts/test.sh'
        input(message: 'Is Test Successful and ready to Continue', ok: 'Yes and Continue to Publish and Execute')
      }
    }
    stage('Deliver and Stop') {
      steps {
        sh 'bash ./jenkins/scripts/deliver.sh'
        input(message: 'Have you tested REACT Application', ok: 'Yes, I\'ve successfully tested, continue to stop the sever...')
        sh 'base ./jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    CI = 'true'
    HOME = '.'
    PORT_NUMBER = '9090'
  }
}