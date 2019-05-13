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
                    def triggerCause = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.IssueCommentCause)
                    if (triggerCause) {
                        echo("Who wrote: " +
                            "\"${triggerCause.comment}\", which matches the " +
                            "\"${triggerCause.triggerPattern}\" trigger pattern.")
                    }
                    echo 'this is the triggerCause -> ${triggerCause} end'
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