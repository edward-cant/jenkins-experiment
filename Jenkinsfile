pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!' 
            }
        }

        stage('Email Test') {
            steps {
                sendEmail("jenkins-experiment sending test email")
            }
        }
    }
}

void sendEmail(String subject, String message) {
    String[] recipients = [
        'edward.cant',
        'edward.cant+test2',
    ]

    for (String recipient : recipients) {
        emailext(
            subject: subject,
            mimeType: 'text/html',
            to: recipient + '@calnexsol.com',
            body: message
        ) 
    }
}
