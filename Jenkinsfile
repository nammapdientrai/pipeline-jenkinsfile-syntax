NAME_CONTAINER = 'java-jdk'

pipeline {
    agent any

    stages {
        stage('Check exist container') {
            steps {
                script {
                    def f = ""

                    f = sh(returnStdout: true, script: 'docker ps -aq -f status=exited -f name=java-jdk')
                    
                    echo "${f}"
                }
            }
        }
    }
}
