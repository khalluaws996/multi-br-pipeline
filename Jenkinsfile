pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('food')
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Generate a unique container name
                    def containerName = "food-con-${env.BUILD_ID}"

                    // Run the new container
                    sh "docker run -dt --name ${containerName} -p 90:80 food"
                }
            }
        }
    }
}
