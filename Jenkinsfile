pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Build the Docker image
                    def ecommImage = docker.build('ecomm')
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Stop and remove the existing container if it exists
                    try {
                        sh 'docker stop ecomm-con || true'
                        sh 'docker rm ecomm-con || true'
                    } catch (Exception e) {
                        echo 'No existing container to stop and remove'
                    }

                    // Run the new container
                    sh 'docker run -dt --name ecomm-con -p 60:80 ecomm'
                }
            }
        }
    }
}
