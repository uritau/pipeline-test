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
                        pullRequest.comment("Hello! I am the CI, I have triggered a new build because " +
                        "${triggerCause.userLogin} asked it, " +
                        "you can find the build [here](${currentBuild.absoluteUrl}).")
                    }
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