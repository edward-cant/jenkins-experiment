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
                        sendEmail(recipient, "Build Greeting", "Hello ${recipient}")
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
