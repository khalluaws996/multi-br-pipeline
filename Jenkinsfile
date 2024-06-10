pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    def customImage = docker.build('food')
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Stop and remove the existing container if it exists
                    try {
                        sh 'docker stop food-con || true'
                        sh 'docker rm food-con || true'
                    } catch (Exception e) {
                        echo 'No existing container to stop and remove'
                    }

                    // Run the new container
                    sh 'docker run -dt --name food-con -p 90:80 food'
                }
            }
        }
    }
}
