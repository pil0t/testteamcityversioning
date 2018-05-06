pipeline {
  agent any
   
  stages {

    
      stage('input') {
            steps {
                input(
                    id: 'userInput', message: 'Text goes here', parameters: [
                        [ $class: 'DropdownAutocompleteParameterDefinition', name: 'MyName', dataprovider: [
                            [$class: 'InlineJsonDataProvider', autoCompleteData: '[{"id":"1"},{"id":"2"}]'
                ], 
                        
        displayExpression: 'id',
        valueExpression: 'id'
                        ]]])
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
