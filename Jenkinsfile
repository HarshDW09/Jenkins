pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build Autimation Tool
                echo 'Building the code using Maven'
               
              
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                
                echo 'Running unit tests using JUnit
                // Run integration tests using Selenium
                echo 'Running integration tests using Selenium'
              
            }
        }
        stage('Code Analysis') {
            steps {
                // Analyse the code using SonarQube
                echo 'Analysing the code using SonarQube
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
        }
        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server using AWS CLI
                echo 'Deploying the application to a production server using AWS CLI'
     
            }
        }
    }
    post {
        always {
            // Send notification emails at the end of test and security scan stages
            echo 'Sending notification emails'
            emailext attachLog: true, body: '${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}', subject: '${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}', to: 'harshinfinity09@gmail.com'
        }
    }
}
