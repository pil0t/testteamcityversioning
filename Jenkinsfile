pipeline {
  agent any
   
  stages {

    
      stage("Interactive_Input") {
            steps {
                script {

                    // Variables for input
                    def inputConfig
                    def inputTest

                    // Get the input
                    def userInput = input(
                            id: 'userInput', message: 'Enter path of test reports:?',
                            parameters: [

                                    AutoCompleteStringParameterDefinition(defaultValue: 'None',
                                            description: 'Path of config file',
                                            name: 'Config', 
  dataProvider: RemoteDataProvider(autoCompleteUrl: 'https://raw.githubusercontent.com/pil0t/testteamcityversioning/master/test.json')),
                                    string(defaultValue: 'None',
                                            description: 'Test Info file',
                                            name: 'Test'),
                            ])

                    // Save to variables. Default to empty string if not found.
                    inputConfig = userInput.Config?:''
                    inputTest = userInput.Test?:''

                    // Echo to console
                    echo("IQA Sheet Path: ${inputConfig}")
                    echo("Test Info file path: ${inputTest}")

                    // Write to file
                    writeFile file: "inputData.txt", text: "Config=${inputConfig}\r\nTest=${inputTest}"

                    // Archive the file (or whatever you want to do with it)
                    archiveArtifacts 'inputData.txt'
                }
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
