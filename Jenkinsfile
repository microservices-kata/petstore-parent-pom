def mvnImage = 'maven:3.5.0-jdk-8-alpine'
def mvnFolder = '/opt/m2'

pipeline {
    agent {
        docker {
            reuseNode true
            image "maven:3.5.0-jdk-8-alpine"
            args "-v ${mvnFolder}:/root/.m2"
        }
    }
    stages {
        stage('代码更新') {
            steps {
                checkout scm
            }
        }
        stage('部署pom文件') {
            steps {
                sh "mvn clean install"
            }
        }
    }
}
