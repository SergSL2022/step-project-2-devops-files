pipeline {
    agent{ label "ip-177" }

    triggers {
        pollSCM ignoreChanges: [specificPath('https://github.com/SergSL2022/step-project-2-devops-files.git')]
    }

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

    post {
        always {
            deleteDir() 
        }
    }
}