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
                script {
                    try {
                        sh """
                        pwd
                        ls -la
                        npm run test
                        """
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        error("Tests failed: ${e}")
                    }
                }
            }
        }
        
        stage('Build Docker image') {
            steps {
                catchError(stageResult: 'UNSTABLE', buildResult: 'SUCCESS') {
                    echo "Building Docker image"
                    sh """
                        pwd
                        ls -la
                        npm run build
                        pwd
                        ls -la
                        docker build -t react-app:v.0.0.${BUILD_NUMBER} .
                        docker images
                    """
                }
            }
        }
        
       
        stage('Push Docker image') {
            steps {
                catchError(stageResult: 'UNSTABLE', buildResult: 'SUCCESS') {
                    echo "Pushing Docker image to Dockerhub registry"
                    sh """
                    pwd
                    ls -la
                    """
                }
            }
        }
    }
}