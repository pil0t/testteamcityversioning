pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '3', artifactNumToKeepStr: '3'))
    }
    agent none
    stages {
        stage('input') {
            steps {
                input(
                    id: 'userInput', message: 'Text goes here', parameters: [
                        [ $class: 'DropdownAutocompleteParameterDefinition', name: 'MyName', displayExpression: 'id', valueExpression: 'id', dataprovider: [
                            [$class: 'InlineJsonDataProvider', autoCompleteData: '[{"id":"1"},{"id":"2"}]']]]])
           }
        }
    }
}
