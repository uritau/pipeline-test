pipeline {
    agent any
    triggers {
        issueCommentTrigger('.*test this.*')
    }
    stages {
        stage('Build') {
            steps {
                def now = new Date()
                def time = now.format("yyMMdd.HHmm", TimeZone.getTimeZone('UTC'))
                echo 'Building..'
                pullRequest.comment( '${time} + Building again because stuff')
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}