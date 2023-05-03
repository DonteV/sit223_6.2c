pipeline {
    agent any
    
    stages {
        stage('Build') {
            tools {
                maven 'Maven'
            }
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            tools {
                maven 'Maven'
            }
            steps {
                bat 'mvn test'
                bat 'mvn integration-test'
            }
        }
        stage('Code Analysis') {
            steps {
                bat 'npm install -g jshint'
                bat 'jshint src'
            }
        }
        stage('Security Scan') {
            steps {
                bat 'npm install -g nsp'
                bat 'nsp check'
            }
        }
        stage('Deploy to Staging') {
            steps {
                bat 'mkdir C:\\opt\\myapp'
                bat 'xcopy /s /y target\\myapp.war C:\\opt\\myapp'
                bat 'ssh user@staging-server "mkdir -p /opt/myapp"'
                bat 'pscp C:\\opt\\myapp\\myapp.war user@staging-server:/opt/myapp'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                bat 'ssh user@staging-server "java -jar /opt/myapp/myapp.war & ping -n 30 localhost > nul"'
                bat 'curl http://staging-server:8080/myapp/test'
            }
        }
        stage('Deploy to Production') {
            when {
                branch 'master'
            }
            steps {
                bat 'mkdir C:\\opt\\myapp'
                bat 'xcopy /s /y target\\myapp.war C:\\opt\\myapp'
                bat 'ssh user@production-server "mkdir -p /opt/myapp"'
                bat 'pscp C:\\opt\\myapp\\myapp.war user@production-server:/opt/myapp'
            }
        }
    }
}
