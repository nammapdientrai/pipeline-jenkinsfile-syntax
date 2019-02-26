pipeline {
    agent none

    environment {
        def foo = "Check exist container"
    }

    stages {
        stage('Check exist container') {
            steps {
                sh "echo ${foo}"
            }
        }
    }
}
