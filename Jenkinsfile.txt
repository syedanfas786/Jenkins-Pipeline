pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Build was successful"
                echo "Maven Tool Used"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Unit and Integration Tests passed"
                echo "Junit Tool Used"
            }
            post {
                success {
                    mail to: "syedanfas786@gmail.com",
                    subject: "Test status success",
                    body: "Test was success",
                    attachLog: true
                    // attachmentsPattern: '**/console-log.txt'
                }
                failure {
                    mail to: "syedanfas786@gmail.com",
                    subject: "Test status failure",
                    body: "Test was failure",
                    attachLog: true
                     // attachmentsPattern: '**/console-log.txt'
        
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Code Analysis completed"
                echo "Junit Tool Used"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Security Scan completed"
                echo "Jmeter Tool Used"
            }
            post {
                success {
                    mail to: "syedanfas786@gmail.com",
                    subject: "Security scan status success",
                    body: "Security scan was success",
                    attachLog: true
                    // attachmentsPattern: '**/console-log.txt'
                }
                failure {
                    mail to: "syedanfas786@gmail.com",
                    subject: "Security scan status failure",
                    body: "Security scan was failure",
                    attachLog: true
                    // attachmentsPattern: '**/console-log.txt'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deployed to Staging"
            }
        }
        stage('Integration Tests on Staging') {
            steps { 
                echo "Integration Tests on Staging passed"
                echo "Jmeter Tool Used"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deployed to Production"
            }
        }
    }
}
