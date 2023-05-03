pipeline {
    agent any
    
    stages {
        stage('Build') {
            tools {
                maven 'Maven'
            }
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            tools {
                maven 'Maven'
            }
            steps {
                sh 'mvn test'
                sh 'mvn integration-test'
            }
        }
        stage('Code Analysis') {
            steps {
                sh 'npm install -g jshint'
                sh 'jshint src'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'npm install -g nsp'
                sh 'nsp check'
            }
        }
        stage('Deploy to Staging') {
            steps {
                sh 'ssh user@staging-server "mkdir -p /opt/myapp"'
                sh 'scp target/myapp.war user@staging-server:/opt/myapp'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                sh 'ssh user@staging-server "java -jar /opt/myapp/myapp.war & sleep 30"'
                sh 'curl http://staging-server:8080/myapp/test'
            }
        }
        stage('Deploy to Production') {
            when {
                branch 'main'
            }
            steps {
                sh 'ssh user@production-server "mkdir -p /opt/myapp"'
                sh 'scp target/myapp.war user@production-server:/opt/myapp'
            }
        }
    }
}
