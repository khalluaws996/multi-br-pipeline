pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Build the Docker image
                    def loginImage = docker.build('login')
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Stop and remove the existing container if it exists
                    try {
                        sh 'docker stop login-con || true'
                        sh 'docker rm login-con || true'
                    } catch (Exception e) {
                        echo 'No existing container to stop and remove'
                    }

                    // Run the new container
                    sh 'docker run -dt --name login-con -p 70:80 login'
                }
            }
        }
    }
}
