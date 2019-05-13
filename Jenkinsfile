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
                        echo("Hello! I am the CI, I haveve triggered a new build because " +
                        "\"${triggerCause.userLogin} wrote: " +
                        "\"> ${triggerCause.comment}" +
                        "\", you can find the build [here](${currentBuild.absoluteUrl}).")
                    }
                    echo ("this is the triggerCause -> " +
                    "\"${triggerCause}\" end")
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