pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!' 
            }
        }

        stage('Stage 2') {
            steps {
                print "parameter: ${fruit}"
            }
        }

        stage('Stage 3') {
            steps {
                print "parameter: ${emails}"
            }
        }

        stage('Stage 4') {
            steps {
                script {
                    "${emails}".split("\n").each { recipient ->
                        // print it for now
                        print "recipient: ${recipient}"
                    }
                }
            }
        }

        stage('Email') {
            steps {
                script {
                    "${emails}".split("\n").each { recipient ->
                        sendBuildInformationEmail(recipient, "Build Greeting", "Hello ${recipient}")
                        //sendEmail(recipient, "Build Greeting", "Hello ${recipient}")
                    }
                }
            }
        }

    }
}

void sendEmail(String recipient, String subject, String message) {
    emailext(
        subject: "${currentBuild.projectName}: ${subject}",
        mimeType: 'text/html',
        to: recipient,
        body: message
    ) 
}

void sendBuildInformationEmail(String recipient, String subject, String line) {
    String message = """
        Hello ${recipient},

        ${line}

        Here is some information about the current build:

        - Project Name: ${currentBuild.projectName}
        - Build Number: ${currentBuild.number}
        - Build Status: ${currentBuild.result}
        - Duration: ${currentBuild.durationString}
        - Build URL: ${currentBuild.absoluteUrl}

        Best Regards,
        Your Jenkins Build System
    """

    sendEmail(recipient, subject, message)
}
