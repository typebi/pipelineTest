pipeline {
    agent {
        node {
            label 'master'
        }
    }
    stages {
        stage('Git Progress') {
            steps {
                git branch: 'main', url: 'https://github.com/typebi/pipelineTest/'
                slackSend (channel: '#testchannel', color: '#008000', message: "GIT CONNECT")
            }
        }
        stage('Build') {
            steps {
                sh './gradlew clean build'
                slackSend (channel: '#testchannel', color: '#008000', message: "BUILD SUCCESS")
            }
        }
        stage('Test') {
            steps {
                sh 'echo test'
                slackSend (channel: '#testchannel', color: '#008000', message: "RUN TEST")
            }
        }
        stage('Deploy') {
            steps {
                sh 'java -jar --server.port=8180 build/libs/Practice.jar'
                slackSend (channel: '#testchannel', color: '#008000', message: "DEPLOY SUCCESS")
            }
        }
    }
}
