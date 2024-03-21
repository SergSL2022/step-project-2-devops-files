pipeline {
    agent{ label "ip-177" }

    stages{
        stage('Checkout') {
            steps {
                echo "Checkout stage"
                git branch: "main",
                    credentialsId: "Gitlab",
                    url: "https://gitlab.com/serhiy.slipchuk/step-project-2.git"
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
                npm install
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
                npm run test
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