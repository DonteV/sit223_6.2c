pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Compiling code using Maven'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Unit and Integration Tests are running using JUnit...'
            }
            post {
                success {
                    emailext body: 'Unit and Integration Tests are successful.',
                    subject: 'Unit and Integration Tests Success',
                    to: 's222258066@deakin.edu.au'
                }
                failure {
                    emailext body: 'Unit and Integration Tests failed.',
                    subject: 'Unit and Integration Tests Failed',
                    to: 's222258066@deakin.edu.au'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running code analysis using SonarQube...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan using OWASP ZAP...'
            }
            post {
                success {
                    emailext body: 'Security scan was successful.',
                    subject: 'Security Scan Success',
                    to: 's222258066@deakin.edu.au'
                }
                failure {
                    emailext body: 'Security scan failed.',
                    subject: 'Security Scan Failed',
                    to: 's222258066@deakin.edu.au'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'The application is being deployed to an AWS EC2 instance...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Integration Tests on Staging are being run using Cypress...'
            }
            post {
                success {
                    emailext body: 'Integration Tests on Staging are successful.',
                    subject: 'Integration Tests on Staging Success',
                    to: 's222258066@deakin.edu.au'
                }
                failure {
                    emailext body: 'Integration Tests on Staging failed.',
                    subject: 'Integration Tests on Staging Failed',
                    to: 's222258066@deakin.edu.au'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'The application is being deployed to an AWS EC2 production server...'
            }
        }
    }
}
