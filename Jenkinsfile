NAME_CONTAINER_JDK = 'java-jdk'

NAME_CONTAINER_MYSQL = 'volume-mysql'
USERNAME_MYSQL ='root'
PASSWORD_MYSQL='123456789'
DATABASE_NAME = 'test'

pipeline {
    agent any

    stages {
        stage('Check exist container JDK') {
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

        stage('Check exist container MYSQL') {
            steps {
                sh "docker exec java-mysql /usr/bin/mysqldump -u root --password=123456789 test > /home/namth22/backup.sql"

                script {
                    def exist = "0"
                   
                    exist = sh(returnStdout: true, script: "docker ps -aq -f name=${NAME_CONTAINER_MYSQL}")
                    //status = sh(returnStdout: true, script: "docker ps -aq -f status=running -f name=${NAME_CONTAINER_JDK}")
                    
                    if (exist != "") {
                        sh "docker container stop ${NAME_CONTAINER_MYSQL}"
                        sh "docker container rm ${NAME_CONTAINER_MYSQL}"
                    }
                }

                sh "docker run --name=${NAME_CONTAINER_MYSQL} -e MYSQL_ROOT_PASSWORD=${PASSWORD_MYSQL} --link java-mysql -d mysql"        
            }
        }
    }
}
