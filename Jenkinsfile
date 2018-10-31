pipeline {
    agent { docker { image 'maven:3.3.3' } }

    stages {
        stage('Build') {
            steps {
                sh 'printenv'
            }
        }
        stage('Test') {
            echo "test"
        }
    }
}

    try {
        userInput = input(
            id: 'Proceed1', message: 'Was this successful?', parameters: [
            [$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']
            ])
    } catch(err) { // input false
        def user = err.getCauses()[0].getUser()
        userInput = false
        echo "Aborted by: [${user}]"
    }
    if (userInput == true) {
        // do something
        echo "this was successful"
    } else {
        // do something else
        echo "this was not successful"
        currentBuild.result = 'FAILURE'
    } 
