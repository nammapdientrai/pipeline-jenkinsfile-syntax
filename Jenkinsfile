NAME_CONTAINER = 'java-jdk'

pipeline {
    agent any

    
    environment {
        def foo = "Check exist container"
    }

    stages {
        stage('Check exist container') {
            steps {
                sh "[docker ps -aq -f status=exited -f name=java-jdk]=${foo}"
                echo "${foo}"
            }
        }
    }
}
