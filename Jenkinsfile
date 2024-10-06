
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                    // Specify your build tool here, for example Maven:
                    // sh 'mvn clean install'
                }
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests...'
                    // Specify your test tool here, for example JUnit or TestNG
                    // sh 'mvn test'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Performing code analysis...'
                    // Specify your code analysis tool, for example SonarQube:
                    // sh 'sonar-scanner'
                }
            }
        }
        
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan...'
                    // Specify your security scan tool, for example Snyk:
                    // sh 'snyk test'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging environment...'
                    // Specify the deployment commands for staging, for example:
                    // sh 'kubectl apply -f staging-deployment.yaml'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging...'
                    // Run integration tests on the staging environment
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production environment...'
                    // Specify the deployment commands for production, for example:
                    // sh 'kubectl apply -f production-deployment.yaml'
                }
            }
        }
    }

    post {
        success {
            emailext body: "Build succeeded. Check the logs for more details.",
                     subject: "Jenkins Build Success Notification",
                     to: "mrunaldas5@gmail.com"
        }
        failure {
            emailext body: "Build failed. Please check the logs and fix the issues.",
                     subject: "Jenkins Build Failure Notification",
                     to: "mrunaldas5@gmail.com"
        }
        unstable {
            emailext body: "Build was unstable. Check for potential issues.",
                     subject: "Jenkins Build Unstable Notification",
                     to: "mrunaldas5@gmail.com"
        }
        always {
            emailext body: "Build completed. Check the logs.",
                     subject: "Jenkins Build Completed",
                     to: "mrunaldas5@gmail.com"
        }
    }
}
