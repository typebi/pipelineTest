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
                slackSend (channel: '#testchannel', color: '#008000', message: "RUN TEST 1")
            }
        }
        stage('Deploy') {
            steps {
                sh 'java -jar --server.port=8180 java -jar build/libs/demo-0.0.1-SNAPSHOT.jar'
                slackSend (channel: '#testchannel', color: '#008000', message: "DEPLOY SUCCESS")
            }
        }
    }
}
