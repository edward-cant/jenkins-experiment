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

        stage('Stage 2b') {
            steps {
                print "parameter: ${build_minor}"
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
        ${line}<br/>
        <br/>
        Here is some information about the current build:<br/>
        <br/>
        - Project Name: ${currentBuild.projectName}<br/>
        - Build Number: ${currentBuild.number}<br/>
        - Build Status: ${currentBuild.result}<br/>
        - Duration: ${currentBuild.durationString}<br/>
        - Build URL: ${currentBuild.absoluteUrl}<br/>
        <br/>
        Best Regards,<br/>
        Your Jenkins Build System<br/>
    """

    sendEmail(recipient, subject, message)
}
