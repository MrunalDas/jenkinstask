pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Specify the build automation tool, e.g., Maven
                sh 'mvn clean install'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Specify a testing tool, e.g., JUnit or TestNG
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                // Specify a code analysis tool, e.g., SonarQube
                sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Specify a security scanning tool, e.g., OWASP ZAP or Snyk
                sh 'snyk test'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Use a deployment tool, e.g., AWS CLI, kubectl, or Docker
                sh 'aws deploy my-staging-app'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                // Perform integration tests on staging, e.g., Postman or Selenium
                sh 'mvn integration-test'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                // Deploy to production, e.g., AWS CLI or kubectl
                sh 'aws deploy my-prod-app'
            }
        }
    }

    post {
        always {
            echo 'Sending email notification...'
            // Email notification
            mail to: 'mrunaldas5@gmail.com',
                 subject: "Build ${currentBuild.fullDisplayName}: ${currentBuild.currentResult}",
                 body: "Build completed with status: ${currentBuild.currentResult}. Check Jenkins for more details.",
                 attachmentsPattern: '**/target/*.log'
        }

        success {
            echo 'Build succeeded!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
