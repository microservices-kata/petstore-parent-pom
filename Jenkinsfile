def gitRepo = 'https://github.com/microservices-kata/petstore-parent-pom.git'
def mvnImage = 'maven:3.5.0-jdk-8-alpine'
def mvnFolder = '/opt/m2'

node {
    stage('代码更新') {
        checkout scm: [$class: 'GitSCM', branches: [[name: '*/master']],
                      userRemoteConfigs: [[url: gitRepo]]]
    }
    docker.image("${mvnImage}").inside("-v ${mvnFolder}:/root/.m2") {
        stage('部署pom文件') {
            sh 'mvn clean install'
        }
    }
}
