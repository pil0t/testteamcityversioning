pipeline {
  agent any
   
  stages {
    stage('Example') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob,admin,pil0t"
                parameters: [choice(name: 'RELEASE_SCOPE', choices: 'patch\nminor\nmajor', description: 'What is the release scope?')]
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
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
