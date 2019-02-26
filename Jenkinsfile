NAME_CONTAINER_JDK = 'java-jdk'

pipeline {
    agent any

    stages {
        stage('Check exist container') {
            steps {
                script {
                    def exist = "0"
                   
                    exist = sh(returnStdout: true, script: "docker ps -aq -f name=${NAME_CONTAINER_JDK}")
                    //status = sh(returnStdout: true, script: "docker ps -aq -f status=running -f name=${NAME_CONTAINER_JDK}")
                    
                    if (exist != "") {
                        sh 'docker container stop java-jdk'
                        sh 'docker container rm java-jdk'
                    }

                    sh "docker run --name ${NAME_CONTAINER_JDK} -d -v /opt/tomcat/.jenkins/workspace/java-full-pipeline/demojenkins/target:/home -i openjdk"        
                }
            }
        }
    }
}
