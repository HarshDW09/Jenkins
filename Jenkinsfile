pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build Autimation Tool// I am editing this//I am editing this agin
                echo 'Building the code using Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests using JUnit'
                echo 'Running integration tests using Selenium'
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Analysing the code using SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                // Scan the code using OWASP ZAP
                echo 'Scanning the code using OWASP ZAP'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server using AWS CLI
                echo 'Deploying the application to a staging server using AWS CLI'
            
            }
        }
        stage('Integration Tests on Staging') {
            steps {
            
                echo 'Running integration tests on the staging environment using Selenium'
             
            }
        }              //HD
        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server using AWS CLI
                echo 'Deploying the application to a production server using AWS CLI'
     
            }
        }
    }
   post {
    always {
        // Send notification emails at the end of test stage
        echo 'Sending notification emails';
        emailext attachLog: true, to: 'harshinfinity09@gmail.com', subject: "Build: ${currentBuild.currentResult}", body: "Status: ${currentBuild.currentResult}";
    }
}
}
