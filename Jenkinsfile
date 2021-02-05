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
            }
        }
        stage('Test Slack') {
            steps {
                slackSend (channel: '#testchannel', color: '#008000', message: "GIT CONNECT")
            }
        }
        stage('Build') {
            steps {
                sh 'gradle clean build'
                slackSend (channel: '#testchannel', color: '#008000', message: "BUILD SUCCESS")
            }
        }
    }
}
