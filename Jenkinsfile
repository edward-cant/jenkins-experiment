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

        // stage('Email Test') {
        //     def recipients = "${notification emails}"
            
        //     steps {
        //         // Read the 'notification email' multi line string parameter
        //         // and send emails to each of those users
        //         // def recipients = """
        //         //     edward.cant@calnexsol.com
        //         //     edward.cant+test2@calnexsol.com
        //         // """
        //         // Get the parameter from the jenkins server build config

        //         recipients.split().each { recipient ->
        //             sendEmail(recipient, "jenkins-experiment", "sending test email")
        //         }
        //     }
        // }
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
