pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "c:\\codepath"
        TESTING_ENVIRONMENT = "test-env"
        PRODUCTION_ENVIRONMENT = "5.1p"
    }
    stages {
        stage("Build") {
            steps {
                echo "fetch the source code from the directory path specified by the environment variable: $DIRECTORY_PATH"
                echo "compile the code and generate any necessary artifacts"
            }
        }
        stage("Test") {
            steps {
                echo "running unit tests..."
                echo "running integration tests..."
            }
        }
        stage("Code Quality Check") {
            steps {
                echo "check the quality of the code..."
            }
        }
        stage("Deploy") {
            steps {
                echo "deploy the application to a testing environment specified by the environment variable: $TESTING_ENVIRONMENT"
            }
        }
        stage("Approval") {
            steps {
                    script {
                        echo "awaiting approval..."
                        sleep(time: 10, unit: "SECONDS")
                        echo "Approved. Continuing..."
                }
            }
        }
        stage("Deploy to Production") {
            steps {
                echo "deploying code to production environment: $PRODUCTION_ENVIRONMENT"
            }
        }
    }
}
