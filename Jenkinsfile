pipeline
{
    agent any
    stages
    {
        stage('Build')
        {
            steps
            {
                echo 'Compiling code using Maven'
            }
        }

        stage('Unit and Integration Tests')
        {
            steps
            {
                echo 'Unit and Integration Tests are running using JUnit...'
            }
            post
            {
                success
                {
                    emailext attachLog: true,
                    subject: 'Unit and Integration Tests Success',
                    body: 'Unit and Integration Tests are successful.',
                    to: 's222258066@deakin.edu.au'
                }
                failure
                {
                    emailext attachLog: true,
                        subject: 'Unit and Integration Tests Failed',
                        body: 'Unit and Integration Tests failed.',
                        to: 's222258066@deakin.edu.au'
                }
            }
        }

        stage('Code Analysis')
        {
            steps
            {
                echo 'Running code analysis using SonarQube...'
            }
        }

        stage('Security Scan')
        {
            steps
            {
                echo 'Running security scan using OWASP ZAP...'
            }
            post
            {
                success
                {
                    emailext attachLog: true,
                    subject: 'Unit and Integration Tests Success',
                    body: 'Unit and Integration Tests are successful.',
                    to: 's222258066@deakin.edu.au'
                }
                failure
                {
                    emailext attachLog: true,
                        subject: 'Unit and Integration Tests Failed',
                        body: 'Unit and Integration Tests failed.',
                        to: 's222258066@deakin.edu.au'
                }
            }
        }

        stage('Deploy to Staging')
        {
            steps
            {
                echo 'The application is being deployed to an AWS EC2 instance...'
            }
        }

        stage('Integration Tests on Staging')
        {
            steps
            {
                echo 'Integration Tests on Staging are being run using Cypress...'
            }
            post
            {
                success
                {
                    emailext attachLog: true,
                    subject: 'Integration Tests on Staging Success',
                    body: 'Integration Tests on Staging are successful.',
                    to: 's222258066@deakin.edu.au'
                }
                failure
                {
                    emailext attachLog: true,
                        subject: 'Integration Tests on Staging Failed',
                        body: 'Integration Tests on Staging failed.',
                        to: 's222258066@deakin.edu.au'
                }
            }
        }

        stage('Deploy to Production')
        {
            steps
            {
                echo 'The application is being deployed to an AWS EC2 production server...'
            }
        }
    }
}
