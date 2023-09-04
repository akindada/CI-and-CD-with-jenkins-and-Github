pipeline {
    agent any
    
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "mv1"
    }
  
  stages{  
   stage('Build') {
     steps {
       //Perform build steps here
       //We will be using Maven as our build automation tool
       sh 'pwsh-- clean Build'
   }}
   stage('Unit and Integration Tests') {
       steps {
       //Run unit tests to ensure the code functions as expected
       //Run integration tests to ensure the different components of the application work together as expected
       //We will be using JUnit and TestNG for test automation
       sh 'mv1 test'
   }}
   stage('Code Analysis') {
       steps {
       //Integrate a code analysis tool to analyse the code and ensure it meets industry standards
       //We will be using SonarQube for our code analysis
       sh 'mv1 sonar:sonar'
   }}
   stage('Security Scan') {
      steps {
       //Perform a security scan on the code using a tool to identify any vulnerabilities
       //We will be using OWASP ZAP for our security scan
       sh 'zap-baseline.py -t http://example.com'
   }}
   stage('Deploy to Staging') {
       steps {
       //Deploy the application to a staging server (e.g., AWS EC2 instance)
       sh 'aws deploy'
   }}
   stage('Integration Tests on Staging') {
      steps {
       //Run integration tests on the staging environment to ensure the application functions as expected in a production-like environment
       sh 'mv1 test'
   }}
   stage('Deploy to Production') {
      steps {
       //Deploy the application to a production server (e.g., AWS EC2 instance)
       sh 'aws deploy'
   }}
   //Configure the pipeline to send notification emails to a specified email address at the end of test and security scan stages
            
  }
}
post {
    success {
        emailext body: '''Your Jenkins build is successful. The changes are deployed successfully.''',
                 subject: 'Jenkins build and deployment success',
                 to: 'developer1@example.com, developer2@example.com'
    }
    failure {
        emailext body: '''Your Jenkins build and deployment failed. Please check the logs for more details.''',
                 subject: 'Jenkins build and deployment failure',
                 to: 'developer1@example.com, developer2@example.com'
    }
}
