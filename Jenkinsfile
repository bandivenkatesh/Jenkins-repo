pipeline {
    agent any

    environment {
        imageName = "pet-clinic"
        imageTag = "v1"
    }

    stages {
        stage('step-one') {
            steps {
                echo 'Hello-World'
            }
        }
        stage('step-two') {
            steps {
                sh 'hostname'
            }
        }
        stage('step-three') {
            steps {
                script {
                    // Clone the repository
                    git 'https://github.com/bandivenkatesh/spring-petclinic-own.git'

                    // Build the Java application
                    sh 'mvn clean package'

                    // Build the Docker image with a specific name and tag
                    docker.build("${imageName}:${imageTag}")
                }
            }
        }
    }
}
// this is a practise pipeline
// updating for trigerring build in jenkins
