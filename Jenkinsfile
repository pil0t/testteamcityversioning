pipeline {
  agent any
  currentBuild.description = "#${BUILD_NUMBER}, branch ${BRANCH}"
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
