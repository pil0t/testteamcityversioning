pipeline {
  agent any
  stages {
    stage('Build') {
      environment {
        FF = 'r'
        TT = 'rr'
      }
      parallel {
        stage('Build') {
          steps {
            echo 'Building..'
            sh 'dotnet build TestMe'
          }
        }
        stage('error') {
          steps {
            echo 'xxxx'
            build 'testteamcityversioning'
          }
        }
      }
    }
    stage('Test') {
      steps {
        echo 'Testing..'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}