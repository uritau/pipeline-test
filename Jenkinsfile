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
                        echo("Build was started by ${triggerCause.userLogin}, who wrote: " +
                            "\"${triggerCause.comment}\", which matches the " +
                            "\"${triggerCause.triggerPattern}\" trigger pattern.")
                    }

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