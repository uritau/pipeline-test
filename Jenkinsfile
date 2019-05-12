pipeline {
    agent any
    triggers {
        issueCommentTrigger('.*test this.*')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                script {
                    pullRequest.comment( 'Building again because stuff')
                }
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