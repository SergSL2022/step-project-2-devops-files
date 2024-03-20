pipeline {
    agent{ label "ip-177" }

    stages{
        stage('Checkout') {
            steps {
                echo "Checkout stage"
                sh """
                ip a
                pwd
                ls -la
                """
            }
        }

        stage('Install') {
            steps {
                echo "Installing dependencies"
                sh """
                pwd
                ls -la
                """
            }

        }

        stage('Run tests') {
            steps {
                echo "Running tests"
                sh """
                pwd
                ls -la
                """
            }
        }

        stage('Build Docker image') {
            steps {
                echo "Building Docker image"
                sh """
                pwd
                ls -la
                """
            }
        }

        stage('Push Docker image') {
            steps {
                echo "Pushing Docker image to Dockerhub registry"
                sh """
                pwd
                ls -la
                """
            }
        }
    }
}