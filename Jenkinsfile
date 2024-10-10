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

        stage('Email Test') {
            steps {
                recipients = "${notification emails}"
                recipients.split().each { recipient ->
                    sendEmail(recipient, "jenkins-experiment", "sending test email")
                }
            }
        }
    }
}

void sendEmail(String recipient, String subject, String message) {
    // String[] recipients = [
    //     'edward.cant',
    //     'edward.cant+test2',
    // ]

    // for (String recipient : recipients) {
        emailext(
            subject: subject,
            mimeType: 'text/html',
            to: recipient,
            body: message
        ) 
    // }
}
