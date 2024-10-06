pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Your build steps here
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                // Your testing steps here
                echo 'Testing...'
            }
        }
    }
    post {
        always {
            echo 'This will always run after the pipeline stages'
        }
        success {
            emailext(
                subject: "Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Good news! The build succeeded. See the build details at ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                to: 'mrunaldas5@gmail.com'
            )
        }
        failure {
            emailext(
                subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Unfortunately, the build has failed. Please review the details at ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                to: 'mrunaldas5@gmail.com'
            )
        }
    }
}

