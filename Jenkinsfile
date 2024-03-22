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
              catchError(message: 'This stage is unstable', stageResult: 'UNSTABLE') {
                    sh """
                        exit 1
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
                CI=false npm run build
                pwd
                ls -la
                docker build -t react-app:v.0.0.${BUILD_NUMBER} .
                docker images
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

    post{
    
    
     error {
            // Цей блок виконується лише в разі виникнення помилки в пайплайні
            // Можна вказати додаткові дії, які потрібно виконати при помилці
            echo 'Tests failed! Stopping the pipeline.'
            currentBuild.result = 'FAILURE' // Позначаємо пайплайн як невдалий
            error 'Tests failed!' // Цей рядок вказує Jenkins, що потрібно зупинити пайплайн
        }

    }
}