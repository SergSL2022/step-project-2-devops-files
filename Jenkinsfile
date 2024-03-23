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
                catchError(stageResult: 'UNSTABLE', buildResult: 'SUCCESS') {
                    echo "Installing dependencies"
                    sh """
                        pwd
                        ls -la
                        npm install
                        ls -la
                    """
                }
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
                echo "Building Docker image"
                sh """
                    pwd
                    ls -la
                    CI=false npm run build
                    pwd
                    ls -la
                    docker build -t serhiyslipchuk/danit:v.0.0.${BUILD_NUMBER} .
                    docker images
                    cd ~/
                    mkdir artifacts
                    docker save -o /home/vagrant/artifacts/danit_v.0.0.${BUILD_NUMBER}.tar serhiyslipchuk/danit:v.0.0.${BUILD_NUMBER}
                    """
            }
        }
        
       
        stage('Push Docker image') {
            steps {
                echo "Pushing Docker image to Dockerhub registry"
                withCredentials([usernamePassword(credentialsId: 'Dockerhub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USER')]) {
                    sh """
                        docker login -u ${DOCKER_USER} -p ${DOCKER_PASSWORD}
                        docker push serhiyslipchuk/danit:v.0.0.${BUILD_NUMBER}
                    """
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: "/home/vagrant/artifacts/danit_v.0.0.${BUILD_NUMBER}.tar", allowEmptyArchive: true
        }
    }
}