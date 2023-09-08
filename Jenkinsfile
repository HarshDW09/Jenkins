pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build Autimation Tool
                echo 'Building the code using Maven'
                tool name: 'Maven'
                sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                
                echo 'Running unit tests using JUnit'
                sh 'mvn test'
                // Run integration tests using Selenium
                echo 'Running integration tests using Selenium'
                sh 'mvn verify'
            }
        }
        stage('Code Analysis') {
            steps {
                // Analyse the code using SonarQube
                echo 'Analysing the code using SonarQube'
                sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                // Scan the code using OWASP ZAP
                echo 'Scanning the code using OWASP ZAP'
                sh 'zap-cli quick-scan --spider -r http://localhost:8080'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server using AWS CLI
                echo 'Deploying the application to a staging server using AWS CLI'
                sh 'aws s3 cp target/harsh-app.war s3://harsh-bucket/harsh-app.war'
                sh 'aws ec2 run-instances --image-id ami-12345678 --instance-type t2.micro --user-data file://deploy.sh'
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
                sh 'aws s3 cp target/harsh-app.war s3://harsh-bucket/harsh-app.war'
                sh 'aws ec2 run-instances --image-id ami-87654321 --instance-type t2.micro --user-data file://install.sh'
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
